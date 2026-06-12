---
title: "[SOLVED] Noob Python problem"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by apcfreak on 2008-01-20
I just started to learn about Python today, and while going through a tutorial there were example code for the reader to try/modify. Here is one part named one.py :
```
# Area calculation program

print “Welcome to the Area calculation program”
print “–––––––––––––”
print

# Print out the menu:
print “Please select a shape:”
print “1  Rectangle”
print “2  Circle”

# Get the user’s choice:
shape = input(“> “)

# Calculate the area:
if shape == 1:
    height = input(“Please enter the height: “)
    width = input(“Please enter the width: “)
    area = height*width
    print “The area is”, area
else:
    radius = input(“Please enter the radius: “)
    area = 3.14*(radius**2)
    print “The area is”, area
```

As I think I am supposed to do, I open terminal, go to folder where i saved that file (desktop in this case), and say 
```
python one.py
```
and as with most other examples I have tried, there was a syntax error. 
```
mando@admin-desktop:~/Desktop$ python one.py
sys:1: DeprecationWarning: Non-ASCII character '\xe2' in file one.py on line 3, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
  File "one.py", line 3
    print “Welcome to the Area calculation program”
          ^
SyntaxError: invalid syntax

```
I don't know if it is something wrong on my side, or with the code, could anybody help?

---

### Post by -=Ghostlike=- on 2008-01-20
never use ", you should use ' it can't understand double-quotes

Hope that helps

Edit: it's because the double quotes aren't straight down, that is another character, it's not real ASCII

---

### Post by GavinZac on 2008-01-20
did you copy and paste the code? the quotes like so ```
&#8221;
``` dont seem to be standard double quotes, rather the stylised ones not in the ASCII table ... try retyping the quotes like so ```
"
```

---

### Post by SOULRiDER on 2008-01-20
What kind of symbol are you using for " ? It doesnt seem to me like " it looks like youre doing a ''. Try with a single '

---

### Post by apcfreak on 2008-01-20
Ah, that did it. Thanks for the prompt answers, I will be sure to write that down.

---

