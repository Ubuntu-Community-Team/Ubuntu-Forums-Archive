---
title: "command line calculator"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by DrPppr242 on 2007-05-04
Does anyone know of a calculator program that can be run from the command line that allows me to do addition subtraction multiplication and division bare minimum?

---

### Post by Acglaphotis on 2007-05-04
Quick one in python,copy to text editor, rename calc.py and run from terminal (python /path/to/calc/calc.py)

```

# calculator program

# NO CODE IS REALLY RUN HERE, IT IS ONLY TELLING US WHAT WE WILL DO LATER
# Here we will define our functions
# this prints the main menu, and prompts for a choice
def menu():
    #print what options you have
    print "Welcome to calculator.py"
    print "your options are:"
    print " "
    print "1) Addition"
    print "2) Subtraction"
    print "3) Multiplication"
    print "4) Division"
    print "5) Quit calculator.py"
    print " "
    return input ("Choose your option: ")
    
# this adds two numbers given
def add(a,b):
    print a, "+", b, "=", a + b
    
# this subtracts two numbers given
def sub(a,b):
    print b, "-", a, "=", b - a
    
# this multiplies two numbers given
def mul(a,b):
    print a, "*", b, "=", a * b
    
# this divides two numbers given
def div(a,b):
    print a, "/", b, "=", a / b
    
# NOW THE PROGRAM REALLY STARTS, AS CODE IS RUN
loop = 1
choice = 0
while loop == 1:
    choice = menu()
    if choice == 1:
        add(input("Add this: "),input("to this: "))
    elif choice == 2:
        sub(input("Subtract this: "),input("from this: "))
    elif choice == 3:
        mul(input("Multiply this: "),input("by this: "))
    elif choice == 4:
        div(input("Divide this: "),input("by this: "))
    elif choice == 5:
        loop = 0
    else:
         print "Im asking for numbers, not letters, dont be a smartass."

print "Thankyou for using calculator.py!"

```

---

### Post by DrPppr242 on 2007-05-04
thanks very much, I happen to be trying to learn pyhton myself, do you mind if I mess around with your source code and try to add so more options ect?

---

### Post by Acglaphotis on 2007-05-04
Yeah, you can, but it is not my source code, its available freely on a tutorial for python. And i happen to be trying to learn python too. Small world huh?

-Acgla

---

### Post by DrPppr242 on 2007-05-04
> **Acglaphotis said:**
> Yeah, you can, but it is not my source code, its available freely on a tutorial for python. And i happen to be trying to learn python too. Small world huh?

-Acgla

could you post a link to that tutorial site?

---

### Post by Acglaphotis on 2007-05-04
Sure:

[http://www.sthurlow.com/python/lesson01/]("http://www.sthurlow.com/python/lesson01/")

---

