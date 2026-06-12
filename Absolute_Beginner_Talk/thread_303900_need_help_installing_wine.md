---
title: "need help installing wine"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by slirock on 2006-11-21
I am in the terminal I try to run update this is the message its giving me


W: You may want to run apt-get update to correct these problems
john@barnabas:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

can you help me on the steps i need to take i am new at this

Thank You

---

### Post by cptjaben on 2006-11-21
Looks like you need to run the command with super user power try:

```
sudo apt-get update
```

as far as installing Wine goes, I believe one can use [Automatix]("http://www.getautomatix.com/") which will let you install it using a graphical interface. hope this helps

---

### Post by rlozano on 2006-11-21
> **cptjaben said:**
> Looks like you need to run the command with super user power try:

```
sudo apt-get update
```

as far as installing Wine goes, I believe one can use [Automatix]("http://www.getautomatix.com/") which will let you install it using a graphical interface. hope this helps

or go to this site is you want a manual installation of wine: 

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by ctrlcctrlv on 2006-11-21
wine is useful but is limiting. 

there is a handy program called cedega 
its commercial and well supported if you pay for it

[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by slirock on 2006-11-21
I would i try installing progams that use windows to ubuntu usinf wine? For example Interent Explore

---

### Post by bodhi.zazen on 2006-11-21
> **slirock said:**
> I would i try installing progams that use windows to ubuntu usinf wine? For example Interent Explore

Try this: [How to wine](http://doc.gwos.org/index.php/HowToWine)

---

