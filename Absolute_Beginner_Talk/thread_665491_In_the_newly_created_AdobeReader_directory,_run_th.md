---
title: "In the newly created AdobeReader directory, run the INSTALL script"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by gleble on 2008-01-12
Embarrassed to ask,but how?

---

### Post by PmDematagoda on 2008-01-12
Why don't you just add the Medibuntu repositories according to this [guide]("https://help.ubuntu.com/community/Medibuntu"), run:-
```
sudo apt-get update
```
and install Acrobat Reader using:-
```
sudo apt-get install acroread
```

That should install Acrobat Reader.

---

### Post by gleble on 2008-01-12
I get
```
neil@neil-laptop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package acroread
neil@neil-laptop:~$ 


```

I have downloaded  adobe and changed to theAdobeReader directory. How do I run the install file? See question

---

### Post by PmDematagoda on 2008-01-12
Post the result of:-
```
cat /etc/apt/sources.list
```

---

### Post by PmDematagoda on 2008-01-12
> I have downloaded  adobe and changed to theAdobeReader directory. How do I run the install file? See question


And if you wish to install without the repositories, could you post the error message you get when running the install file?

---

### Post by gleble on 2008-01-12
Thats the problem.How do I run the install file?

---

### Post by PmDematagoda on 2008-01-12
Either:-
```
sh nameoffile
```
or
```
./nameoffile
```

---

### Post by gleble on 2008-01-12
Thanks.Trouble with ubuntu is theres  nowhere to easily find out these little things

---

### Post by Joeb454 on 2008-01-12
That's not trouble with Ubuntu. I'm sure it'd be the same for any Linux/Unix system

---

