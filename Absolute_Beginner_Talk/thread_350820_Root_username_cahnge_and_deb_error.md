---
title: "Root username cahnge and deb error"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-01
First Question: How can I change the name of the root user?
Second question: when I am trying to enter a deb http:// and so on, this error pops up: bash: deb: command not found
what is it??
Thanks!:confused:

---

### Post by ayed on 2007-02-01
Wow, so its not that easy?

---

### Post by ayed on 2007-02-01
Does someone have something against me? !!

---

### Post by jd65pl on 2007-02-01
There is no reason for you to change the 'root' user name and you shouldn't really be doing it. Is there any reason why you would like to change this users name?
Try rewording the second part of your question it is not clear no one has anything against you they probably just don't understand what you are asking.

---

### Post by ayed on 2007-02-01
Ok, I am trying to install xgl, but when I try to do the follwoing:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse
i get the follwoing error:
bash: deb: command not found
whats wrong?

---

### Post by jd65pl on 2007-02-01
You are supposed to add that line to your sources.list not run it in the terminal. Do the following:

```
gksudo gedit /etc/apt/sources.list
```

Then at the bottom of the file add in the below or change as appropriate

>  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse


Then do

```
sudo apt-get update
sudo apt-get upgrade
```

---

