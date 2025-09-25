def matrix_subtract(A, B):
    n = len(A)
    m = len(A[0])
    result = [[0.0]*m for _ in range(n)]
    for i in range(n):
        for j in range(m):
            result[i][j] = A[i][j] - B[i][j]
    return result

def matrix_multyply(A,B):
    n = len(A)
    m = len(B[0])
    p = len(B)
    result = [[0.0]*m for _ in range(n)]
    for i in range(n):
        for j in range(m):
            s = 0.0
            for k in range(p):
                s += A[i][k] * B[k][j]
                result[i][j] = s
    return result

def scalar(n, number):
    I = [[0.0]*n for _ in range(n)]
    for i in range(n):
        I[i][i] = number
    return I

def trace(A):
    n = len(A)
    s = 0.0
    for i in range(n):
        s+= A[i][i]
    return s

def inverse_fadeev(A):
    n = len(A)
    
    current_A = [row.copy() for row in A]
    
    previous_B = None
    last_p = None
    
    for k in range(1, n+1):
        sum = 0
        for i in range(n):
            sum += current_A[i][i]
        p_k = sum/k
            
        B_k = []
        
        for i in range(n):
            row = []
            for j in range(n):
                if i == j:
                    row.append(current_A[i][j]- p_k)
                else:
                    row.append(current_A[i][j])
            B_k.append(row)
            
        if k == n-1:
            previous_B = [row.copy() for row in B_k]
            
        if k == n:
            last_p = p_k
            
        if k < n:
            
            new_A = []
            for i in range(n):
                new_row= []
                for j in range(n):
                    sum_1 = 0
                    for k_index in range(n):
                        sum_1 += A[i][k_index] * B_k[k_index][j]
                    new_row.append(sum_1)
                new_A.append(new_row)
            current_A = new_A     
            
    inv = [[previous_B[i][j]/last_p for j in range(n)]for i in range(n)] 
    return inv              
                    
def print_matrix(M):
    for row in M:
        print(row)
        
A = [
    [2,-1,0],
    [-1,2,-1],
    [0,-1,2]
]
        
        
print("մատրիցա A=")
print_matrix(A)

invA = inverse_fadeev(A)

print("հակադառդզ")
print_matrix(invA)
