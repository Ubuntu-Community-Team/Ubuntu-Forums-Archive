---
title: "compile error"
date: 2006-01-15
forum: Apple PPC Users
---

### Post by nilsk on 2006-01-15
when I try to compile krecipes-0.9.1 I get this error:

checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

what is wrong?


NilsK

---

### Post by BoneKracker on 2006-03-27
Sounds like you might need source for X as well, but I don't know why that wouldn't have been pulled in as a dependency.

---

### Post by Sutekh on 2006-03-27
Because he is compiling from source code, not using apt-get, nilsk must resolve dependancies manually

To compile this program you are going to need
```
sudo apt-get install kdelibs4-dev
```

However, you may not have been aware but **krecipes** is in the **universe** repository so you can install it using apt-get.

First enable the universe repository, by editing your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
sudo nano /etc/apt/sources.list
```
and remove any '#' in front of lines that contain **universe**.  Save the file (Ctrl+O) and exit (Ctrl+X). 

Then install krecipes the easy way
```
sudo apt-get update
sudo apt-get install krecipes
```

---

