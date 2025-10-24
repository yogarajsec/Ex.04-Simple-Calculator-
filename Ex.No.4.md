# Ex04 Simple Calculator - React Project
## Date:24.10.25

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM
### calculator.js
```
import React, { useState } from 'react';
import './calculator.css';

const Calculator = () => {
  const [input, setInput] = useState('');

  // Handle button clicks
  const handleClick = (value) => {
    setInput(input + value);
  };

  // Handle clear button click
  const handleClear = () => {
    setInput('');
  };

  // Handle backspace button click (remove last character)
  const handleBackspace = () => {
    setInput(input.slice(0, -1));
  };

  // Handle equals button click
  const handleEqual = () => {
    try {
      // Evaluate the expression manually
      const result = evaluateExpression(input);
      setInput(result.toString());
    } catch (error) {
      setInput('Error');
    }
  };

  // Function to evaluate expression
  const evaluateExpression = (expr) => {
    // Validate and parse the input expression
    // Split the expression into numbers and operators
    const operators = ['+', '-', '*', '/'];
    let numbers = [];
    let currentNum = '';

    // Iterate through the expression and separate numbers and operators
    for (let i = 0; i < expr.length; i++) {
      const char = expr[i];

      if (operators.includes(char)) {
        if (currentNum !== '') {
          numbers.push(parseFloat(currentNum));
        }
        numbers.push(char); // Push operator
        currentNum = ''; // Reset current number
      } else {
        currentNum += char; // Accumulate the number
      }
    }

    // Push the last number
    if (currentNum !== '') {
      numbers.push(parseFloat(currentNum));
    }

    // Now we can process the numbers and operators manually
    // First process multiplication and division
    for (let i = 1; i < numbers.length - 1; i++) {
      if (numbers[i] === '*' || numbers[i] === '/') {
        const left = numbers[i - 1];
        const right = numbers[i + 1];
        const result = numbers[i] === '*' ? left * right : left / right;
        numbers.splice(i - 1, 3, result); // Replace the operation with the result
        i--; // Adjust the index after modification
      }
    }

    // Then process addition and subtraction
    let result = numbers[0];
    for (let i = 1; i < numbers.length; i += 2) {
      const operator = numbers[i];
      const value = numbers[i + 1];
      if (operator === '+') {
        result += value;
      } else if (operator === '-') {
        result -= value;
      }
    }

    return result;
  };

  return (
    <div className="calculator">
      <div className="display">{input || '0'}</div>
      <div className="buttons">
        <button onClick={handleClear} className="clear">C</button>
        <button onClick={handleBackspace} className="backspace">⌫</button> {/* Remove button */}
        <button onClick={() => handleClick('/')}>/</button>
        <button onClick={() => handleClick('*')}>*</button>
        
        <button onClick={() => handleClick('7')}>7</button>
        <button onClick={() => handleClick('8')}>8</button>
        <button onClick={() => handleClick('9')}>9</button>
        <button onClick={() => handleClick('+')}>+</button>
        <button onClick={() => handleClick('4')}>4</button>
        <button onClick={() => handleClick('5')}>5</button>
        <button onClick={() => handleClick('6')}>6</button>

        <button onClick={() => handleClick('-')}>-</button>
        <button onClick={() => handleClick('2')}>2</button>
        <button onClick={() => handleClick('3')}>3</button>
        <button onClick={() => handleClick('1')}>1</button>
        <button onClick={handleEqual} className="equal">=</button>
        <button onClick={() => handleClick('00')} className="zero-zero">00</button>
        <button onClick={() => handleClick('0')} className="zero">0</button>
        <button onClick={() => handleClick('.')}>.</button>
      </div>
      <footer className="footer">
        <p>&copy; 2025 Simple Calculator </p>
          <p>Archana K (212222240011)</p>
      </footer>
    </div>
  );
};

export default Calculator;
```
### calculator.css
```
.calculator {
    width: 100%;
    max-width: 350px;
    margin: 40px auto;
    padding: 25px;
    border-radius: 12px;
    background: #f7f7f7;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  }
  
  .display {
    font-size: 32px;
    padding: 20px;
    text-align: right;
    background: #fff;
    margin-bottom: 20px;
    border-radius: 8px;
    border: 1px solid #ccc;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  button {
    padding: 20px;
    font-size: 18px;
    background-color: #e0f7fa;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s;
  }
  
  button:hover {
    background-color: #b2ebf2;
  }
  
  .clear {
    background-color: #ef5350;
    color: white;
  }
  
  .clear:hover {
    background-color: #e53935;
  }
  
  .equal {
    background-color: #4caf50;
    color: white;
    grid-column: span 1;
  }
  
  .equal:hover {
    background-color: #388e3c;
  }
  
  .zero {
    grid-column: span 2;
  }
  ```

## OUTPUT
![image](https://github.com/user-attachments/assets/db575e1d-2132-45a4-8c79-3c5a6a2c6cda)


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
