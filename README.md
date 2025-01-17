### **1. Generation of Eisenstein Integers (EIs):**
- **EIs Representation:** Complex numbers of the form \( a + b\omega \), where \( \omega = e^{2\pi i/3} \).
- **Finite Field Mapping:** Coefficients \( a, b \) are taken modulo \( p = 257 \) to ensure computations remain within a finite field.
- **Polynomial Construction:** Each \( a + b\omega \) is represented as a polynomial \( c_0 + c_1w + c_2w^2 \) modulo \( p \).

---

### **2. Determination of Points on an Elliptic Curve:**
- **Elliptic Curve Equation:** The curve is defined as \( y^2 \equiv x^3 + b \mod p \).
- **Satisfying Polynomials:** Coefficients \( (x, y) \) that satisfy the curve equation are collected.
- **Distinct Coefficients:** The unique \( y \)-coordinates are extracted for further computations.

---

### **3. Affine Mapping and Coefficient Transformation:**
- **Affine Transformation:** For each satisfying polynomial \( (x, y) \):
  - A constant term \( x \) and a coefficient \( y \) are computed.
  - Transformations \( x \cdot \text{constant} \) and \( y \cdot \text{coefficient} \mod p \) are applied to generate new points.
- **Points Storage:** Transformed points are stored in \( R \) for subsequent point addition.

---

### **4. Point Addition on the Elliptic Curve:**
- **Addition Function:** Implements the elliptic curve point addition formula:
  - Handles cases where \( P \neq Q \) and \( P = Q \) (doubling).
  - Returns \( None \) for invalid additions.
- **Iterative Addition:** For each pair \( P, Q \) in \( R \), addition is performed, generating a new list of points.

---

### **5. Extraction of Distinct Values:**
- **Modulo Reduction:** Resultant \( (u, v) \) points are reduced modulo 256.
- **Unique Selection:** Ensures no repeated values in \( Sx \) (output S-box values).

---

### **6. Non-Linearity Calculation:**
- **Walsh Transform Matrices:** Large transformation matrices (using \( \pm1 \) mappings) are generated iteratively.
- **Boolean Function Transformation:** Input values from \( Sx \) are transformed via matrix multiplications.
- **Maximum Deviation:** Non-linearity is calculated as \( 128 - (\text{max deviation}/2) \) for each Boolean function.
- **Averaged NL Value:** The average non-linearity of the S-box is computed.

---

### **7. Output and Verification:**
- **S-Box Construction:** \( Sx \) forms the substitution table.
- **Parameters Logging:** Outputs the values of \( a \), \( b \), and computed non-linearity \( l \).
- **Performance Metrics:** Reports distinct \( Sx \) values and non-linearity, ensuring the S-box meets cryptographic standards.

---

### **Key Features of the Approach:**
1. **Eisenstein Integers:** Enhances algebraic structure for secure mapping.
2. **Elliptic Curves:** Adds robustness through complex modular arithmetic.
3. **Affine Mapping:** Increases non-linearity and diffusion.
4. **Non-Linearity Evaluation:** Ensures the S-box's resistance to linear attacks.
