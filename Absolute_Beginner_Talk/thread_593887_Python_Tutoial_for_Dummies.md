---
title: "Python Tutoial for Dummies"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bribaetz on 2007-10-27
[SIZE="5"]Python For Dummies[/SIZE]
[SIZE="3"][COLOR="Red"]First things first please note while you can run from the terminal, i would recommend geany ide downloaded by going into  add new programs (or synaptic) and select all available programs or whatever and go to programing.[/COLOR][/SIZE]
[SIZE="3"]so I'm guessing you have never programed before, so thats where I'm going to start.[/SIZE]
[SIZE="5"]History Of Python[/SIZE]
Python is an open source language which means anyone can edit it and anyone one can use it for free.
Python is not named after the snake but after Monty Python, and has been around since 1992 i believe. 
Python is an easier language  that is higher level which means that you can write a security system but not an operating system. Python is great for first time programmers but not  so great for big programs  that you would need "C++ or C" for.
[SIZE="5"]Lets Get Started[/SIZE]
First open your geany program and click new then click document  then find python under file type.
first type this
```
##Python is easy to learn 
```
then press enter

now this
```
print "hello, world"
```
press enter agian

you should have this
```
[COLOR="Silver"]##[/COLOR]Python is easy to learn [COLOR="Red"] 
print[/COLOR] "Hello, World!"
```

which will output this
```
hello, world
```

the  reason "## python is easy to learn" didn't show up is because it was behind the comment tag and the "python is easy to learn" is not the important part the "##" is the tage put text behind it and when someone views the code they will know what each line means with the "##" in the program.
the "print" puts any thing thats after print in "" on the screen.

[SIZE="4"]and thats you first program now your officially  a programer[/SIZE]
[SIZE="7"]Get ready for section 2[/SIZE]

---

### Post by bribaetz on 2007-10-27
please make comments brief and please dont flame, feel free to add to this guide or add links to other guides and i cant take full credit i used some others guides to build mine off of.
but do feel free to comment please do i would like to know if it helps at all

---

### Post by bribaetz on 2007-10-27
[SIZE="6"]Section 2[/SIZE]
[SIZE="4"]2nd Program[/SIZE]
[SIZE="3"][COLOR="DarkRed"]Have a good feel for the print and comment commands?
did learning that wet your apatite?
ready to learn a little more?[/COLOR]  [/SIZE]
Open a new geany document and change the file type to python.
Okay first type 
```
## variables 
```
okay so you know the comment tag. 
so i don't have to explain this one.

Now press enter and type this
```
print "Hello!"
```
Again you know this, right?

Heres something you don't know.
```
name = raw_input ("whats you name?")
```
"name" is the variable it just hold information that the user of the program assigns to it, like your name but it could have just as easily been  "n".
raw_input means the user inputs after the text.
("") go around the text that asks for the name the text inside it is not important.

Next type
```
print "hello," ,name
```
",name" is just  the variable it prints the information assigned to the variable that is after the print command the text comes first or last depending on the place you want the variable.
 
or you could have put it like this
```
print "hello" ,name ,"the knight"
```

save compile then run and see if it works.
[SIZE="6"] Get ready for section 3[/SIZE]

---

### Post by bribaetz on 2007-10-27
[python tut wikibook ]("http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python/Contents")
is a great python tut
also [this]("http://www.sthurlow.com/python/lesson02/") is okay

---

### Post by bribaetz on 2007-10-27
[SIZE="6"]section 3[/SIZE]
[SIZE="5"]another variable program[/SIZE]
```
 
b = 0
b = input ("input # of the month your born in: ")
if b == 4:
 print "i think your a touris"
if b == 5:
 print "you MAY be a touris"
if b > 5:
 print "your not a touris" 
if b < 4:
 print "your not a touris" 
```
this is our next program it will tell you if it thinks your a touris zodiac i think i spelled it wrong

if b == 4
4 is the month if is saying well if this is this or if this is not this then  this does this.
you must indent to have a working program every thing that needs if for it to work  must have an indention form if but things that do not depend on if to work correctly must not be indented.
b = 0
b starts out as 0 and when you input it changes b to that number. and that all you need to have this program to work 
[SIZE="7"]get ready for section 4[/SIZE]

---

### Post by bribaetz on 2007-10-27
[SIZE="7"]section 4
EXAM[/SIZE]
```
 a = 0
print "press 1 for addition"
print "press 2 for subtraction"
print "press 3 for multiplication"
print "press 4 for divsion"
a = input ("operation:")
if a == 1:
 n = input("Number: ")
 b = input("number: ")
 y = n + b
 print n, "+", b, "=", y
if a == 2:
 n = input("Number: ")
 b = input("number: ")
 y = n - b
 print n, "-", b, "=", y
if a == 3:
 n = input("Number: ")
 b = input("number: ")
 y = n * b
 print n, "*", b, "=", y
if a == 4:
 n = input("Number: ")
 b = input("number: ")
 y = n / b
 print n, "/", b, "=", 
```
try to figure out what each line of code does i will leave the answer at the bottom if you didn't
get it look over previous sections again.






its a simple calculator to get this i made a simple menu out of  if statements and if you select  any of 4 number to the menu it will take you to the next step the step to do the operation you chose  because each if picks up on a number  and  that starts the operation

---

### Post by bribaetz on 2007-10-27
```

         print "Calculator 7.04"
c = input ("number:")
b = raw_input ("operation:")
a = input ("number:")
p = "-"
r = "+"
t = "*"
y = "/"
if b == y:
 print c, b, a, "=", c / a
if b == t:
 print c, b, a, "=", a * c
if b == r:
 print c, b, a, "=", a + c
if b == p:
 print c, b, a, "=", a - c 
```
this is another example of virtually the same program

---

### Post by bribaetz on 2007-10-27
once i touch up on this particular part of python we will move one to loops

---

### Post by bribaetz on 2007-10-27
[SIZE="7"]section 5[/SIZE]
```
#this will print 1 - 20
a = 0
while a <= 20:
	print a
	a = a +1
```
"while" continues to do every thing indented from it until the a stops meeting its requirements
[LIST=1]
== means = to
<= greater than or = to
>= less than or = to
!= not = to
< greater than
> less than
[/LIST]
a continues growing until it gets bigger than 20 and there for stops the loop you can use loops for almost any thing and will see them in most programs.
there are many different loops and many ways to use them this is a small example. play with loops in different programs.
```
 a = 0
loop = 1
while loop == 1:
 print "press 1 for addition"
 print "press 2 for subtraction"
 print "press 3 for multiplication"
 print "press 4 for divsion"
 print "press 5 for exiting"
 a = input ("operation:")
 if a == 1:
  n = input("Number: ")
  b = input("Number: ")
  y = n + b
  print n, "+", b, "=", y
 elif a == 2:
  n = input("Number: ")
  b = input("Number: ")
  y = n - b
  print n, "-", b, "=", y
 elif a == 3:
  n = input("Number: ")
  b = input("Number: ")
  y = n * b
  print n, "*", b, "=", y
 elif a == 4:
  n = input("Number: ")
  b = input("number: ")
  y = n / b
  print n, "/", b, "=", y
 elif  a == 5:
 	loop = 0
 
```
i added a loop to this 5 changes the loop variable to 0 and the while only wants the program to continue if loop is one and there stops the program.

Play with this for a while then 
[SIZE="7"]get ready for section 6[/SIZE]

---

### Post by bribaetz on 2007-10-27
after section 10  this will move on to mid beginner topics so make sure you read all of the tutorial.

---

### Post by LaRoza on 2007-10-27
A "Tutoial" for Dummies? Yep.

Don't follow this thread people, use a [real tutorial]("http://docs.python.org/tut/").

My wiki has others: [http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python)

---

### Post by bribaetz on 2007-10-28
thats kind of mean i thought i done okay. i am shortening it up for the nonprogrammer
and not putting it in sections like that so anyone who fallows it can have python down more quickly there are lots of big long tutorials that make every thing to hard.

---

### Post by Crafty Kisses on 2007-10-28
Thanks!

---

### Post by bribaetz on 2007-10-28
> **Codename said:**
> Thanks!

?

---

### Post by Baby Boy on 2007-10-28
This is the tutorial that I am using to learn Python atm. IMO, it is the most comprehensive (and fun).

[http://www.dickbaldwin.com/tocpyth.htm](http://www.dickbaldwin.com/tocpyth.htm)

---

### Post by LaRoza on 2007-10-28
> **Baby Boy said:**
> This is the tutorial that I am using to learn Python atm. IMO, it is the most comprehensive (and fun).

[http://www.dickbaldwin.com/tocpyth.htm](http://www.dickbaldwin.com/tocpyth.htm)

Looks good. After learning the basics, the Python References on python.org are very useful. I suggest you kee a copy near by. I do.

---

### Post by Perfect Storm on 2007-10-28
I'm closing this thread (will open again) due to some complaints. It will reopen when it's done.


EDIT: I see, there's a duplicate in Programming talk. It's not allowed. So I'll keep this one close, The other one is here: [http://ubuntuforums.org/showthread.php?p=3649338](http://ubuntuforums.org/showthread.php?p=3649338) an investigation will be taken place there.

---

