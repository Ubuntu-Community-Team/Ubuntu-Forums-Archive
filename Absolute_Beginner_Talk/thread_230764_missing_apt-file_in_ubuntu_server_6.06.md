---
title: "missing apt-file in ubuntu server 6.06"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by aroswald1977 on 2006-08-06
I have the following problem searching for needed packages:

$ sudo apt-file search libgdk-1.2.so.0
sudo: apt-file: command not found

](*,)

---

### Post by dusu on 2006-08-06
Hi,

you have to install it with
```
sudo apt-get install apt-file
```
Then do
```
sudo apt-file update
```
and then you can use it as usual

---

### Post by aroswald1977 on 2006-08-06
That worked. Thanks for your help.:KS 

??why did i not just try apt-get before asking?? 
I'll never know

:confused: <--Gnu00813

---

### Post by dusu on 2006-08-07
> **aroswald1977 said:**
> That worked. Thanks for your help.:KS
You're welcome :)

> ??why did i not just try apt-get before asking?? 
A good question that is ;) 

> I'll never know
:confused: <--Gnu00813

Well, I guess it's because these forums are much too much user-friendly :mrgreen:

---

