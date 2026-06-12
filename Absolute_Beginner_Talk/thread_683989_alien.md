---
title: "alien"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by manzoor on 2008-01-31
Hi i can't install alien

it gives me some dependency kind of error I cant remember 


what is it and how to solve it 

thanks

---

### Post by shad0w_walker on 2008-01-31
With out any more information it's gonna be tricky to help you. I suggest you try installing it again and find out exactly what the error was. Give us the bit of information and you should be up and going in no time.

---

### Post by jan quark on 2008-01-31
dependencies are packages on which the actual package you want to install is based 

when you install via the synaptic package manager the dependencies are installed automatically with the package

if the package is not in the synaptic
pls post the error here

but I think it is there

---

### Post by taurus on 2008-01-31
Can you at least post the complete error message when you try to install it from a terminal?

On the other hand, sounds like you don't have any repos available in /etc/apt/sources.list to install any extra apps.

Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark on every line except the last one, Source code, and the Cdrom in the bottom window.  Close it and press Refresh.  Now, see if you can install alien from synaptic this time.

---

### Post by manzoor on 2008-01-31
the error message is

Error: Dependency is not satisfiable: debhelper


I am using the alien.deb file downloaded from ubuntu packages site

---

### Post by PinkFloyd102489 on 2008-01-31
sudo apt-get-f install alien


try that.

---

### Post by Blutack on 2008-01-31
Downloading packages manually from the ubuntu packaging site is not how installing programs is done with ubuntu.
Open a terminal and type in:
sudo apt-get install alien

---

### Post by Perfect Storm on 2008-01-31
> **manzoor said:**
> the error message is

Error: Dependency is not satisfiable: debhelper


I am using the alien.deb file downloaded from ubuntu packages site

Are you without internet connection. If so you need debhelper as well .deb package.
If you have internet you can install alien through synaptic ---> if it isn't there you need to go to Software Sources in System tabs to enable the sources.

---

