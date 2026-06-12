---
title: "Problem whit unistaling a program"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by josue105 on 2007-05-31
Hi, I have downloaded and install limewirelinux in my pc but the program is not working correctly so i decide to uninstall it but i don't know how to do it.

I've tried to do it by Add/Remove but it don't show anything about limewire

---

### Post by madmetal on 2007-05-31
> **josue105 said:**
> Hi, I have downloaded and install limewirelinux in my pc but the program is not working correctly so i decide to uninstall it but i don't know how to do it.

I've tried to do it by Add/Remove but it don't show anything about limewire

how have you installed it? and why its not working?

---

### Post by josue105 on 2007-05-31
I install it like a windows program (duoble click and it install itself) and when i open it, the program load in a white page and i don't see nothin' but a white page

---

### Post by kernel tom on 2007-05-31
hmmm i believe the comand is as follows

sudo apt-get remove limewire-linux

limewire may not be working correctly do to java incompatibilty... so assuming you had java6 installed, doesnt really matter as long as its 5+

run this from the terminal

sudo update-alternatives --all

then go thru the questions, just hitting "return" when u dont know the answer or want to use the current path and whenever you see something to do with java, select the number corresponding to the path with ur most recent java install

should work after taht

---

### Post by josue105 on 2007-06-01
tank's

---

