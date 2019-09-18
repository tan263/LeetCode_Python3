class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        if s==p:
            return True 
        
        l_s = len(s)
        l_p = len(p)
        
        if l_p == 0:
            return False
        
        if l_s == 0:
            if l_p % 2 == 0 and p[slice(1,l_p+1,2)] == "*" *(l_p//2):
                return True
            else:
                return False
        
        match = [[0]*l_p for i in range(l_s)]
        
        match[0][0] = (s[0]==p[0] or p[0]==".")
        
        j = 1
        while j < l_p:
            if p[j]=="*":
                j = j + 2
            else:
                break
        if j > 1:
            match[0][slice(1,j-1,2)] = [True]*(j//2)
            if j <= l_p:
                if p[j-1] == s[0] or p[j-1] == ".":
                    match[0][j-1] = True
        
        for i in range(0, l_s):
            for j in range(0, l_p):
                if i > 0 and j > 0:
                    if match[i-1][j-1] and (s[i] == p[j] or p[j] == "."):
                        match[i][j] = True
                        continue
                    if p[j] == "*":
                        if (p[j-1] == "." or p[j-1] == s[i]) and match[i-1][j-1]:
                            match[i][j] = True
                            continue
                    if match[i-1][j]:
                        if p[j-1] == "." and p[j] == "*":
                            match[i][j] = True
                            continue
                if p[j] == "*":
                    if j > 1:
                        if match[i][j-2]:
                            match[i][j] = True
                            continue
                    if j > 0:
                        if match[i][j-1]:
                            match[i][j] = True
                            continue
                if s[i] == p[j] and p[j-1]=="*" and j > 1 and i > 0:
                    if match[i-1][j-2]:
                        match[i][j] = True
                        #continue        
        
        return match[l_s-1][l_p-1]
