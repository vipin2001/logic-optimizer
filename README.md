# Logic Optimizer
The logic optimizer takes onset and doesn't care function as expression and outputs the optimized function in matrix representation. The number of literals in the expression must also be provided as one of the inputs to the optimize function. The logic optimizer uses the espresso heuristic algorithm. <br>
The function details are given below:<br>
## matrix_formation(function,num_literals)
The function takes two inputs, the function variable is the expression of the function, and the num_literals variable is the number of literal in the expression. It outputs the function in matrix form.
## cost_calculator(func_matrix,num_literals)
The function takes two inputs, the func_matrix variable is the function in matrix form, and the num_literals variable is the number of literal in the expression. It outputs the cost of the function; it ignores the cost of the inverter.
## calc_cofactor(func_matrix,cofactor)
The function takes two inputs, the func_matrix variable is the function in matrix form, and the cofactor variable is the cube in matrix forms. It returns the cofactor of the function w.r.t to the cube in the cofactor variable.
## tautology_check(func_matrix)
It takes a function in matrix form as an input and checks if the function is a tautology or not. If the function is a tautology, it returns true; otherwise, it returns false.
## containment_check(func_matrix,implicant)
The function takes two inputs, the func_matrix variable is the function in matrix form, and the implicant variable is provided in matrix form. The function checks if the function covers the implicant. It returns true if the function covers the implicant; else returns false.
## complement_calc(func_matrix,num_literals)
The function takes two inputs, the func_matrix variable is the function in matrix form, and the num_literals variable is the number of literal in the expression. The function calculates the complement of the given cover and outputs the complement of the cover in matrix form.
## intersection_calculator(func_matrix,cube)
The function takes two inputs, the func_matrix variable is the function in matrix form and the cube variable in matrix form. It returns the intersection of the function and the cube in matrix form.
## expand(onset_matrix,offset_matrix,num_literals)
The function implements the naive expand algorithm in the espresso algorithm.
## reduce(onset_matrix,dcare_matrix,num_literals)
The function implements the naive reduce algorithm in the espresso algorithm.
## irredundant(onset_matrix,dcare_matrix)
The function implements the naive irredundant algorithm in the espresso algorithm.
## essential(func_matrix)
The function takes a cover in matrix form as an input and returns the essential implicants in the matrix form.
## logic_optimizer(onset_matrix,num_literals,dcare_matrix = np.array([]))
The function takes three inputs. The onset_matrix variable is the matrix form of the onset of the function, the num_literals variable is the number of literals in the cover, and dcare_matrix is the don't care set of the function in matrix form if present. It returns the optimized function in the matrix form. To terminate the reduce-expand-irredundant loop in the espresso algorithm, it calculates the cost at each iteration and compares it with the last iteration's cost. If the current cost is equal to or greater than the previous iteration, it returns the optimized circuit of the previous iteration.
## optimize(function,num_literals,dont_care = np.array([])):
The function takes three inputs. Function is the onset set in the expression form, num_literals variable is the number of literals in the cover and dont_care is the dont_care set in the expression form. 
### String Format
The function in expression form can have upto 26 letters represented by english letter. A capital english letter is used for true literal and small letter is used for false literal.<br> For example <br>
01 = "aB"<br>
00 = "ab"<br>
10 = "Ab"<br>
11 = "AB"<br>
For input as sum of product, use the above rule and put a "+" sign in between products. <br>
For example <br>
00 + 11 can be represented as "ab + AB".<br>
Note: The spacing need not be considered; any valid spacing is allowed.<br>