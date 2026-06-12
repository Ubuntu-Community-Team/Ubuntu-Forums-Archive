---
title: "Installing Epson CX4200 Problems"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by johanchangid on 2006-11-17
Hi everyone,

I am trying to install an Epson CX4200 printer for my laptop under ubuntu operating system. If it is under WinXP, it runs well. I downloaded the fifth version of gutenprint as for my epson printer's driver. **Is this driver for EPSON CX4200?**

When installing the driver, I ran the command "./configure" (I follow instructions from README file) and It worked fine. However, once I went to the next step, "Make", it didn't work. There was a message on my terminal saying that "bash: Make: command not found". I don't know what to do now. Does anybody know how to solve it? Please guide me. Thanks alot.

Johan

---

### Post by johanchangid on 2006-11-19
I have already found the answer. Just used 
sudo apt-get install cupsys-driver-gimpprint
sudo apt-get install foomatic-db-engine

sudo apt-get install build-essential  ->this is for makefile

---

### Post by ReaderRat on 2006-11-20
For the future, make does not have a capital 'M", it's lower case. Ubuntu is case-sensitive.

---

