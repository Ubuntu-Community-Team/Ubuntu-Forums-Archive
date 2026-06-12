---
title: "Where can i get Quickfox"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by robbie carrobie on 2007-07-01
Hi everyone, can anyone help me to get quickfox, have a 64 bit Amd on my laptop and had great success with quickfox in the past, just cant remember where i got it - kind regards in advance - robert.

---

### Post by Seisen on 2007-07-01
Here is the repository list, have at it.

[http://packages.quickfox.org/]("http://packages.quickfox.org/")

---

### Post by robbie carrobie on 2007-07-01
wow thanks, do i just paste the code into the terminal window? please forgive my ignorance but i am sure the last time is was part of a third party program, thanks again robert.:D

---

### Post by Seisen on 2007-07-01
Go into the terminal and put this in

```
gksudo gedit /etc/apt/sources.list
``` add the repository for whichever distribution of Ubuntu you are using and then save the file. After that put this in the terminal

```
sudo apt-get update
``` if it doesn't pop up any errors you can tehn apt-get quickfox.

---

