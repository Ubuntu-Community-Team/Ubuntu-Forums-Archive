---
title: "Linux and modems"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by pheonixprime on 2008-04-09
:confused:I have been reading the posts re: modem installations and Ubuntu.

Five years ago I tried a Linux variant. Installed with some difficulty but it booted up and went to a desktop. After a week of trying to get a modem to work with the OS, I nuked it.

Here we are five years later with the Ubuntu OS.  Got an install CD,used it to establish a functional desktop environment. So far , so good. But wait, we STILL cannot find a modem driver for a US Robotics..non winmodem..hardware modem that will work with Ubuntu 7.10

Whats the deal with Linux and modems??

I've been using crappy windows OS's for almost 20 years..but they recognize modems.

Some help please before I pull the pin on this otherwise neat OS

Robert

---

### Post by The Titan on 2008-04-09
we could use a little more information there.  What is the model number of your modem??  I'm pretty sure if its a US Robotics its a winmodem.

---

### Post by SlappyPappy on 2008-04-09
Dude it's easy. Go to here:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Go straight to Alternative Way 1 (using wvdialconf & wvdial).

If you do that and it finds your modem and it's not a software based modem, you'll be up and running in no time. I'm a noob but I got it going using that info.

One thing is when you put in your info for the config file be sure to remove the semi-colons in front of the lines for your user name and password.

Enjoy.   :guitar:

---

### Post by Zeotronic on 2008-04-09
*Dont give up on Ubuntu!* I don't anything about the article that SlappyPappy linked to, but I *do* know, personally, that Conexant modems are supported... you can get the driver free from Dell somewhere.

---

