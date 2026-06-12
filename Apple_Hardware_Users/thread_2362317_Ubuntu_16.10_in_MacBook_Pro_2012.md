---
title: "Ubuntu 16.10 in MacBook Pro 2012"
date: 2017-05-26
forum: Apple Hardware Users
---

### Post by rdutt on 2017-05-26
Hi, 
Since I want python installed in my laptop, I installed Ubuntu 16.10 in my 2012 MacBook Pro with Intel core i7 processor and graphic card HD 4000. 
My touchpad is not working properly. I installed python Jupiter 3.6 version. Talked to apple, they said someone from ubuntu developed driver for the touchpad. 
I have to start using python coding very soon. Seek your help.

---

### Post by howefield on 2017-05-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by &amp;KyT$0P# on 2017-05-26
Why 16.10?  That version will be dead in about a month or two - [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

It might help to see more specs of your computer.  Please install inxi if you don't have it...
```
sudo apt-get install inxi
```
... then run this in Terminal and post the output here -
```
inxi -Fxxz -! 31
```

---

