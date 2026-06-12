---
title: "Running Python Scripts from Terminal"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by sail on 2007-06-26
I'm trying to learn programming in Python with "How to Think Like a Computer Scientist"

I've been saving my files in a folder under the ".py" extension and use the chmod command to make them ready to run. I hadn't had any problems running my scripts until I got to programs that required input from the user. I'm having trouble running them from the terminal, even if I copy and paste the code from the book directly on the text document.

Here's an example:
```
import math
   
def area(radius):
    temp = math.pi * radius**2
    return temp
```

A simple script. I chmod it and run it:
```
rob@squirtle:~$ cd /home/rob/code/
rob@squirtle:~/code$ chmod a+x prac_area.py 
rob@squirtle:~/code$ ./prac_area.py 
./prac_area.py: line 1: import: command not found
./prac_area.py: line 3: syntax error near unexpected token `('
./prac_area.py: line 3: `def area(radius):'
```

This is the same method I've used for other scripts before this. I know I'm probably doing something fundamentally wrong, but what is it?

---

### Post by sail on 2007-06-27
Bump, I guess it dropped to the second page.

---

### Post by freebird54 on 2007-06-27
Sorry for slow response.  Not too sure whether what you're doing SHOULD work, but in any I've done, the first line of the script is

```
#! /usr/bin/env python
```

unless I'm running it with

```
python <name_of_script_file.py>
```

Hope this helps!

(Linux doesn't use file extensions to tell it what's in a file, the .py is for your info!)

---

### Post by sail on 2007-06-27
> **freebird54 said:**
> ```
#! /usr/bin/env python
```

Damn... I KNEW I was doing something fundamentally wrong... I was forgetting that line... Thanks =)

---

### Post by freebird54 on 2007-06-27
Well - at least it wasn't a PYTHON fundamental  :)

(been there - done that - bought the T-shirt)

---

### Post by scruff on 2007-06-27
How to think like a CS is a very nice book considering its free! I used it when I was working on Python fundamentals. Beginning Python (wrox) is also good.

---

### Post by Golyadkin on 2007-06-27
Well, being a computer scientist but not a Python programmer, I guess I will try Beginning Python :)

---

