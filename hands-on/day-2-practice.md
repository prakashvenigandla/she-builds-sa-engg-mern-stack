# Day 2 Practice: Tamil Nadu Electricity Bill Calculator

## Goal

Build a small electricity bill calculator using JavaScript fundamentals:

- Variables and constants
- User input with Node.js `readline`
- Number conversion
- Functions
- `if...else if...else` conditions
- Arithmetic operators
- Template literals

## Problem Statement

Create a program that asks the user for the number of electricity units used in a month and calculates the bill using these practice tariff slabs:

| Units used | Rate for each unit |
| --- | ---: |
| First 100 units | ₹0 |
| Next 100 units (101-200) | ₹2.35 |
| Next 200 units (201-400) | ₹4.70 |
| Above 400 units | ₹6.30 |

This is a learning exercise based on simplified slab rates. It is not an official Tamil Nadu Generation and Distribution Corporation (TANGEDCO) bill calculator.

## Instructions

1. Install Node.js if it is not already installed.
2. Create a file named `day-2-practice.js`.
3. Add the JavaScript below.
4. Run the program from the terminal with `node day-2-practice.js`.
5. Enter different unit values and observe the result.

## Starter Code

```javascript
const readline = require("readline");

function calculateBill(units) {
  let bill = 0;

  if (units <= 100) {
    bill = 0;
  } else if (units <= 200) {
    bill = (units - 100) * 2.35;
  } else if (units <= 400) {
    bill = (100 * 2.35) + ((units - 200) * 4.70);
  } else {
    bill = (100 * 2.35) + (200 * 4.70) + ((units - 400) * 6.30);
  }

  return bill;
}

const terminal = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

terminal.question("Enter the number of units used: ", (unitsInput) => {
  const units = Number(unitsInput);

  if (unitsInput.trim() === "" || Number.isNaN(units) || units < 0) {
    console.log("Please enter a valid non-negative number of units.");
  } else {
    const bill = calculateBill(units);
    console.log(`Units used: ${units}`);
    console.log(`Electricity bill: ₹${bill.toFixed(2)}`);
  }

  terminal.close();
});
```

## Expected Results

| Units | Calculation | Bill |
| ---: | --- | ---: |
| 80 | No charge for the first 100 units | ₹0.00 |
| 150 | `50 × 2.35` | ₹117.50 |
| 300 | `(100 × 2.35) + (100 × 4.70)` | ₹705.00 |
| 500 | `(100 × 2.35) + (200 × 4.70) + (100 × 6.30)` | ₹1,805.00 |

## Think and Try

1. What happens when the user enters `100`, `200`, or `400` units?
2. Why do we subtract `100`, `200`, or `400` before multiplying by a rate?
3. What happens when the user enters text, a negative number, or leaves the input empty?
4. Add a fixed service charge of ₹10 to every valid bill.
5. Rewrite the program so it calculates bills for several customers in one run.

## Submission Checklist

- [ ] The program accepts units from the user.
- [ ] The program uses a function to calculate the bill.
- [ ] The program handles all four unit slabs.
- [ ] The program rejects invalid or negative input.
- [ ] The output shows the units and bill rounded to two decimal places.