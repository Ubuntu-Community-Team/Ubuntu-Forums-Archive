---
title: "ttcp"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-04-20
I need some help with my linux ubuntu. I want to use the application ttcp but i don't know what is the equivalent application in ubuntu.

Somebody knows the answer?

I try to install ntcp but I don't find any result or package to update.

---

### Post by kinalus on 2007-04-20
I think you need the nttcp package. 
A nice way to search for applications when you don't 
know the exact package name is the apt-file utility.
Do this:
# sudo apt-get install apt-file
# sudo apt-file update
then you can look for files with something like this:
# apt-file search ttcp

---

