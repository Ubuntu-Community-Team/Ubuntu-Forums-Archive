---
title: "Executing Python app"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by kool_kat_os on 2007-12-23
I just wrote this app on Python:

[HTML]Python 2.5.1 (r251:54863, Apr 18 2007, 08:51:08) [MSC v.1310 32 bit (Intel)] on win32
Type "copyright", "credits" or "license()" for more information.

    ****************************************************************
    Personal firewall software may warn about the connection IDLE
    makes to its subprocess using this computer's internal loopback
    interface.  This connection is not visible on any external
    interface and no data is sent to or received from the Internet.
    ****************************************************************
    
IDLE 1.2.1      
>>> # Area Calculation Program
>>> print "Welcome to the Area Calculation Program"
Welcome to the Area Calculation Program
>>> print "-------------"
-------------
>>> # Print out this menu:
>>> print "Please select a shape:"
Please select a shape:
>>> print "1 Rectangle"
1 Rectangle
>>> print "2 Circle"
2 Circle
>>> # Get the user's choice:
>>> shape = input("> ")
> 2
>>> # Calculate the Area:
>>> if shape == 1:
	height = input("Please enter the height: ")
	width = input("Please enter the width: ")
	area = height*width
	print "The Area is", area,"units"
else:
	radius = input("Please enter the radius")
	area = 3.14*(radius**2)
	print "The area is", area,"units"

	
Please enter the radius8
The area is 200.96 units
>>> 
[/HTML]

How do I make this app tun in dos on windows? When I click on the file(its named: area.py)the dos pops up for a second and goes away. What am I doing wrong?

---

### Post by kool_kat_os on 2007-12-23
Anybody???

---

