---
title: "[SOLVED] Please Help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by sabirnaz on 2007-12-29
hi,
 I am using Ubuntu for 5 days now. since last night, when I click APPLICATION- ADD/REMOVE..

I get the message---------
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Please help me to rectify this.
Thnx
Sabir

---

### Post by PmDematagoda on 2007-12-29
Do:-
```

sudo apt-get update
```
and
```
sudo apt-get install -f
```
Post the output you get.

---

### Post by atomkarinca on 2007-12-29
In a terminal type:

```
sudo apt-get install -f
sudo apt-get update
```EDIT: you beat me :)

---

### Post by meindian523 on 2007-12-29
Do what it says:

Open Applications>>Accessories>>Terminal

Post
```

cat /etc/apt/sources.list
ls -l /etc/apt/sources.list

```

edit:Everybody beat each other to it.... ;-) :)

---

### Post by sabirnaz on 2007-12-29
Hi,
This is the message I get when i run those 2 commands.


E: Malformed line 51 in source list /etc/apt/sources.list (dist parse)


I am new to Ubuntu. Please bear with me....

thnx for your prompt response.


Sabir

---

### Post by PmDematagoda on 2007-12-29
Open the sources.list file for editing using:-
```
gksudo gedit /etc/apt/sources.list
```
Then go to the 51st line in the file and post it here.

---

### Post by meindian523 on 2007-12-29
Please post your /etc/apt/sources.list and the version of Ubuntu you are using.

To post sources.list,enter

```
cat /etc/apt/sources.list
```

in Applications>>Accessories>>Terminal

@PMD

This is the height of thinking alike.

---

### Post by sabirnaz on 2007-12-29
HI,

deb [http://www.getautomatix.com/apt/gutsy](http://www.getautomatix.com/apt/gutsy) main

thats the 51th line.


Thnx
Sabir

---

### Post by meindian523 on 2007-12-29
I think there needs to be a space between apt and gutsy....

PMD,what say?

edit:
sabirnaz,put a space between the "apt" and "gutsy",then do 

```
sudo apt-get install -f
```

and


```
sudo apt-get update
```

Post back any error messages.

---

### Post by sabirnaz on 2007-12-29
Hi,
 Sorry for being a nob.........
how do i put a space between apt and gutsy

Thnx
Sabir

---

### Post by sabirnaz on 2007-12-29
HI,

Meindian and PMD,    thankyou very much for your help, it was the space between apt and gutsy solved the problem.

Thankyou very much

Sabir

---

### Post by meindian523 on 2007-12-29
1st thread I solved all by myself!Yessss!Please click that star button,Sabir.

---

