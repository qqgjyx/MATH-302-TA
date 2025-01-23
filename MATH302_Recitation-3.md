# $\color{darkblue}{\text{Math 302 - Numerical Analysis}} \newline \color{darkblue}{\text{Recitation \#3 Handout: Some Linear Algebra}}$

**Objective**: This session is a review of essential linear algebra concepts, including:

- Linear independence  
- Existence and uniqueness of solutions for linear systems  
- Rank  
- Eigenvalue decomposition (EVD)  
- Orthogonal decomposition (QR decomposition)  

Complete as much as you can during the recitation. If time runs out, please finish the remaining material as homework.

$\color{red}{\text{Note}}$: **The auto-magic power of VS Code or JetBrains will not be here to help you.** But it does not mean you need to remember every detailed command line we used ---- LLMs always ready to help you. But what you do need is understanding from the top level (to give clear instructions as “leader”).

**There’s lots of IMPORTANT explanation here, for this course and beyond. Actual tasks you’re asked to do are colored $\color{cyan}{\text{cyan}}$ for your convenience, but $\color{red}{\text{read everything}}$. Thanks!**

## $\color{darkblue}{0.} \text{What is Taken as Known}$
  
Some key topics from MATH 105 are assumed to be known. If these concepts feel unfamiliar, please revisit them:

- **Matrix basics**: Operations, transpose, and inverse  
- **Determinants**: Properties and computation  
- **Vector spaces**: Span, basis, and dimension  

$\color{cyan}{\text{Go through}}$ the following terms as a quick check:  

\begin{equation}
\begin{aligned}
&\text{Matrix operations: } A + B, \ cA, \ AB, \ A^{-1}, \ A^T \\
&\text{Determinants: } \det(A), \ \text{and the properties } \det(AB) = \det(A)\det(B), \ \det(A^T) = \det(A) \\
&\text{Vector spaces: } \text{span}(\mathbf{v}_1, \dots, \mathbf{v}_n), \ \dim(V), \ \text{basis of } V \\
\end{aligned}
\end{equation}

## $\color{darkblue}{1.} \text{Linear Independence}$

**Definition**: A set of vectors $\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_n\}$ is linearly independent if:  
\begin{equation}
c_1 \mathbf{v}_1 + c_2 \mathbf{v}_2 + \dots + c_n \mathbf{v}_n = \mathbf{0} \implies c_1 = c_2 = \dots = c_n = 0
\end{equation}  
Otherwise, the vectors are linearly dependent.  

$\color{cyan}{\text{Determine}}$ if the following vectors in $\mathbb{R}^3$ are linearly independent:  
\begin{equation}
\mathbf{v}_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \quad \mathbf{v}_2 = \begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix}, \quad \mathbf{v}_3 = \begin{bmatrix} 1 \\ 3 \\ 2 \end{bmatrix}
\end{equation}

Methods:

- $\color{cyan}{\text{Gaussian elimination}}$ on the linear system $ V \mathbf{c} = \mathbf{0} $
- $\color{cyan}{\text{Determinant}}$ of $ V $ (for suqare $ V $)

## $\color{darkblue}{2.} \text{Existence and Uniqueness of Solutions}$

For a linear system $ A\mathbf{x} = \mathbf{y} $:

- A solution exists if the system is **consistent**, i.e., $ \text{rank}(A) = \text{rank}([A \mid \mathbf{y}]) $.  
- The solution is unique if $ \text{rank}(A) = \text{number of variables} $.  

For the matrix $A$ and vector $\mathbf{y}$ below, $\color{cyan}{\text{determine}}$ if a unique solution exists:  

\begin{equation}
A = \begin{bmatrix} 1 & 1 \\ 1 & 0 \end{bmatrix}, \quad \mathbf{y} = \begin{bmatrix} 34 \\ 21 \end{bmatrix}
\end{equation}

Methods:

- $\color{cyan}{\text{Gaussian elimination}}$ on the linear system $ A \mathbf{x} = \mathbf{y} $
- $\color{cyan}{\text{Inverse}}$ of $ A $ (for square $ A $)

## $\color{darkblue}{3.} \text{Rank}$

**Definition**: The rank of a matrix $A$ is the maximum number of linearly independent rows or columns. It determines the dimension of the column space (range) of $A$.  

$\color{cyan}{\text{Compute}}$ the rank of the following matrix by reducing it to row-echelon form:  
\begin{equation}
A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}
\end{equation}

Methods:

- $\color{cyan}{\text{Reducing to row-echelon form}}$ on $ A $

## $\color{darkblue}{4.} \text{Eigenvalue Decomposition (EVD)}$

**Definition**: For a square matrix $A$, if there exists a scalar $\lambda$ and a non-zero vector $\mathbf{v}$ such that:  
\begin{equation}
A\mathbf{v} = \lambda\mathbf{v},
\end{equation}  
then $\lambda$ is an eigenvalue, and $\mathbf{v}$ is the corresponding eigenvector.  

**Steps to Compute EVD**:

1. Solve $\det(A - \lambda I) = 0$ to find eigenvalues $\lambda$.  
2. For each eigenvalue, solve $(A - \lambda I)\mathbf{v} = \mathbf{0}$ to find eigenvectors.  

$\color{cyan}{\text{Find}}$ the eigenvalues and eigenvectors of:  
\begin{equation}
A = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 1 & 1 & 1 \end{bmatrix}
\end{equation}

Methods:

- $\color{cyan}{\text{Solving}}$ $\det(A - \lambda I) = 0$
- $\color{cyan}{\text{Solving}}$ $(A - \lambda I)\mathbf{v} = \mathbf{0}$

## $\color{darkblue}{5.} \text{Orthogonal Decomposition (QR Decomposition)}$

**Definition**: For a matrix $A$, the QR decomposition expresses it as:  
\begin{equation}
A = QR
\end{equation}  
where:
  
- $Q$ is an orthogonal matrix ($Q^T Q = I$).  
- $R$ is an upper triangular matrix.  

**Steps to Compute QR** (Gram-Schmidt Process):

1. Start with the columns of $A$: $\mathbf{a}_1, \mathbf{a}_2, \dots$.  
2. Compute an orthonormal basis $\mathbf{q}_1, \mathbf{q}_2, \dots$ using:  
   \begin{equation}
   \mathbf{q}_k = \frac{\mathbf{a}_k - \text{Proj}_{\mathbf{q}_1}(\mathbf{a}_k) - \dots - \text{Proj}_{\mathbf{q}_{k-1}}(\mathbf{a}_k)}{\|\mathbf{a}_k - \text{Proj}_{\mathbf{q}_1}(\mathbf{a}_k) - \dots - \text{Proj}_{\mathbf{q}_{k-1}}(\mathbf{a}_k)\|}
   \end{equation}  
3. Construct $Q$ from $\mathbf{q}_1, \mathbf{q}_2, \dots$, and $R$ from the projections.  

$\color{cyan}{\text{Compute}}$ the QR decomposition of:  
\begin{equation}
A = \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\end{equation}

Methods:

- $\color{cyan}{\text{Gram-Schmidt process}}$ on $ A $

## $\color{darkblue}{6.} \text{Note for Students}$

- This material is foundational for numerical methods in interpolation, root-finding, and optimization.  
- Aim to understand the concepts at a high level so you can explain them clearly and confidently.  
- Feel free to use computational tools, but focus on understanding the algorithms and theory behind the computations.
