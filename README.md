# Calculatorreact-Modernweb
# Ex04 Simple Calculator - React Project
## Date:14-03-2026
## Name : A PRAVEEN KISHORE
## Reg No : 212225220074

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
### JSX FILE - 
```
import React, { useState } from 'react';
import './Cal.css';

const Calculator = () => {
  const [input, setInput] = useState('');
  const [result, setResult] = useState('');

  // Handle button clicks for numbers and operators
  const handleClick = (value) => {
    setInput((prev) => prev + value);
  };

  // Clear everything
  const handleClear = () => {
    setInput('');
    setResult('');
  };

  // Delete the last character
  const handleBackspace = () => {
    setInput((prev) => prev.slice(0, -1));
  };

  // Calculate the result
  const handleCalculate = () => {
    try {
      // Evaluate the string expression safely since inputs are controlled
      if (input.trim() === '') return;
      
      // Replace safe visual symbols with actual math operators if needed
      const sanitizedInput = input.replace(/×/g, '*').replace(/÷/g, '/');
      const calculatedResult = eval(sanitizedInput);
      
      setResult(Number(calculatedResult).toLocaleString());
    } catch (error) {
      setResult('Error');
    }
  };

  return (
    <div className="calculator-container">
      <div className="calculator">
        {/* Display Screen */}
        <div className="display">
          <div className="expression">{input || '0'}</div>
          <div className="result">{result}</div>
        </div>

        {/* Keypad */}
        <div className="buttons">
          <button onClick={handleClear} className="btn clear">C</button>
          <button onClick={handleBackspace} className="btn backspace">⌫</button>
          <button onClick={() => handleClick('÷')} className="btn operator">÷</button>
          <button onClick={() => handleClick('×')} className="btn operator">×</button>

          <button onClick={() => handleClick('7')} className="btn">7</button>
          <button onClick={() => handleClick('8')} className="btn">8</button>
          <button onClick={() => handleClick('9')} className="btn">9</button>
          <button onClick={() => handleClick('-')} className="btn operator">-</button>

          <button onClick={() => handleClick('4')} className="btn">4</button>
          <button onClick={() => handleClick('5')} className="btn">5</button>
          <button onClick={() => handleClick('6')} className="btn">6</button>
          <button onClick={() => handleClick('+')} className="btn operator">+</button>

          <button onClick={() => handleClick('1')} className="btn">1</button>
          <button onClick={() => handleClick('2')} className="btn">2</button>
          <button onClick={() => handleClick('3')} className="btn">3</button>
          <button onClick={handleCalculate} className="btn equal-to">=</button>

          <button onClick={() => handleClick('0')} className="btn zero">0</button>
          <button onClick={() => handleClick('.')} className="btn">.</button>
        </div>
      </div>
    </div>
  );
};

export default Calculator;
```
### CSS FILE -
```
/* Centering wrapper */
.calculator-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f4f6f9;
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  box-sizing: border-box;
}

/* Calculator Card */
.calculator {
  width: 100%;
  max-width: 360px; /* Limits size on desktop */
  background-color: #17181a;
  border-radius: 24px;
  padding: 24px;
  box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.15);
}

/* Display styles */
.display {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-end;
  height: 120px;
  padding-bottom: 20px;
  border-bottom: 1px solid #2d2f31;
  word-wrap: break-word;
  word-break: break-all;
}

.expression {
  color: #818589;
  font-size: 1.2rem;
  margin-bottom: 8px;
}

.result {
  color: #ffffff;
  font-size: 2.5rem;
  font-weight: bold;
}

/* Responsive Grid for Buttons */
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
  margin-top: 24px;
}

/* Base button styling */
.btn {
  background-color: #2d2f31;
  color: #ffffff;
  border: none;
  border-radius: 16px;
  padding: 20px 0;
  font-size: 1.25rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.1s ease-in-out;
}

.btn:active {
  transform: scale(0.95);
}

/* Specific button styles */
.btn.operator {
  background-color: #ff9f0a;
  color: white;
}

.btn.clear {
  background-color: #ff3b30;
  color: white;
}

.btn.backspace {
  background-color: #48484a;
}

/* Layout helpers for spanned buttons */
.btn.equal-to {
  grid-row: span 2;
  background-color: #34c759;
  height: 100%;
}

.btn.zero {
  grid-column: span 2;
}

/* Hover effects for desktop users */
@media (hover: hover) {
  .btn:hover { background-color: #3a3d40; }
  .btn.operator:hover { background-color: #e08b07; }
  .btn.clear:hover { background-color: #d63025; }
  .btn.equal-to:hover { background-color: #2db34f; }
}

/* Mobile responsive adjustments */
@media (max-width: 400px) {
  .calculator {
    padding: 16px;
  }
  .btn {
    padding: 16px 0;
    font-size: 1.1rem;
    border-radius: 12px;
  }
  .buttons {
    gap: 8px;
  }
}
```

## OUTPUT
<img width="765" height="802" alt="1" src="https://github.com/user-attachments/assets/e7ba1b28-8e26-4fdc-b866-8f84c45de6e9" />


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
