# String Search : Knuth-Morris-Pratt Algorithm

Develop the String Search by Knuth-Morris-Pratt Algorithm.

We need the failure function to check pattern which characters can skip in order to 
reduce time complexity.

```

def KMPSearch(pattern, text):

    failure = get_failure_array(pattern)

    i = 0
    j = 0
    
    while i < len(text):
        if pattern[j] == text[i]:
            if j == (len(pattern) - 1):
                return True
            j += 1

        elif j > 0:
            j = failure[j - 1]
            continue
        i += 1
    return False

```

```

def get_failure_array(pattern):

    failure = [0]
    i = 0
    j = 1
    while j < len(pattern):
        if pattern[i] == pattern[j]:
            i += 1
        elif i > 0:
            i = failure[i-1]
            continue
        j += 1
        failure.append(i)
    return failure

```