# Newton's Interpolation Calculator (Using p Values)

This Python program implements **Newton's Forward and Backward Interpolation** methods using finite differences. It's designed to compute the estimated value of a function at a given point using known values of the function at equally spaced data points. The user provides the data, and the program calculates and displays the forward and backward interpolation formulas along with their computed results.

---

## 📌 Features

* Accepts custom input for x and y values.
* Automatically generates the forward difference table.
* Displays the difference table in a readable tabular format.
* Computes interpolated function values using:

  * **Newton's Forward Interpolation** (for values near the beginning of the dataset).
  * **Newton's Backward Interpolation** (for values near the end of the dataset).
* Displays the formula used in symbolic form with computed differences and factorial terms.
* Shows intermediate calculations like the value of `p = (x - x0)/h` or `p = (x - xn)/h`.

---

## 📈 Mathematical Background

**Newton's Forward Interpolation Formula:**

$$
f(x) = f(x_0) + p\Delta f(x_0) + \frac{p(p-1)}{2!}\Delta^2 f(x_0) + \cdots
$$

where

* $p = \frac{x - x_0}{h}$
* $h$ is the uniform interval
* $\Delta^n f(x_0)$ are forward differences

**Newton's Backward Interpolation Formula:**

$$
f(x) = f(x_n) + p\nabla f(x_n) + \frac{p(p+1)}{2!}\nabla^2 f(x_n) + \cdots
$$

where

* $p = \frac{x - x_n}{h}$
* $\nabla^n f(x_n)$ are backward differences

These formulas are used when interpolating near the start (forward) or the end (backward) of the dataset.

---

## 🧠 How It Works

1. **User Input:**

   * The program takes comma-separated values for x and y (must be of equal length).
   * Assumes that x values are **equally spaced**.

2. **Forward Difference Table:**

   * Constructs a triangular table showing all successive forward differences of y values.

3. **Interpolation Evaluation:**

   * Uses Newton's formulas to calculate the value of the function at `x = 1` (backward) and `x = 10` (forward).
   * Displays formulas in expanded form with difference values and factorial terms.

4. **Result Display:**

   * Shows interpolated values for both methods.
   * Outputs are formatted to 4 decimal places for clarity.

---

## 🛠️ Code Structure

* `forward_difference_table(x, y)`
  Builds the forward difference table from given data.

* `print_difference_table(x, y, diff_table)`
  Neatly prints the x, y, and all order differences.

* `display_forward_formula(x, y, value)`
  Shows the forward interpolation formula and computes the result for a given value.

* `display_backward_formula(x, y, value)`
  Shows the backward interpolation formula and computes the result for a given value.

* `main()`
  Handles input, calls other functions, and displays the final output.

---

## ▶️ Example Run

```bash
Enter the x values (comma-separated): 0,2,4,6,8,10
Enter the y values (comma-separated): 1,3,7,13,21,31

Difference Table:
x         f(x)      Δ^0      Δ^1      Δ^2      Δ^3      Δ^4      Δ^5
---------------------------------------------------------------------
0.0000    1.0000    2.0000   2.0000   0.0000   0.0000   0.0000
2.0000    3.0000    4.0000   2.0000   0.0000   0.0000
4.0000    7.0000    6.0000   2.0000   0.0000
6.0000    13.0000   8.0000   2.0000
8.0000    21.0000   10.0000
10.0000   31.0000

Newton's Backward Interpolation Formula for x = 1:
P(x) = 31.0000 + (10.0000)(p)/1! + (2.0000)(p)(p+1)/2! + ...
Where p = (x - xn)/h = 1

Newton's Forward Interpolation Formula for x = 10:
P(x) = 1.0000 + (2.0000)(p)/1! + (2.0000)(p)(p-1)/2! + ...
Where p = (x - x0)/h = 5

Final Results:
Value at x=1 using Backward Interpolation f(x): 2.0000  
Value at x=10 using Forward Interpolation f(x): 31.0000
```

---

## ⚠️ Limitations

* Assumes **equally spaced** x values.
* Not suitable for **non-uniform spacing** or large datasets (e.g., 100+ entries).
* Only performs interpolation (not extrapolation beyond provided range).

---

## ✅ Requirements

* Python 3.x
* `numpy` library

Install with:

```bash
pip install numpy
```

---

## 📁 Files

* `interpolation_calculator.py`: Main script with all logic
* (Optional) You can add a sample `input.txt` or integrate with GUI later.

---

## 🚀 Future Improvements

* Add support for Newton's **divided differences** (non-uniform x).
* GUI using Tkinter or PyQt for easier use.
* Graphical plot of interpolation curve.
* Error checking for invalid inputs.

---

## 📄 License

This project is open-source and available under the MIT License. Feel free to use, modify, and share.

---

## 🙌 Contributing

Pull requests are welcome! If you have suggestions or improvements, feel free to fork the repo and create a PR.

---
