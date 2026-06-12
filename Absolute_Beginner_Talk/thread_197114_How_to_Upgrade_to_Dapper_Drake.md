---
title: "How to Upgrade to Dapper Drake"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-06-15
Hope I got the name right. I started with Breezy Badger and my system gave me the option to update and I did . The files were loaded but when I restarted my system my firefox home page was still referring to Breezy Badger.

Is there a feature like the MS help about which displays the version number and name of the Operating system?

Or maybe this is Dapper Drake and I am too stupid to notice.

---

### Post by Jagot on 2006-06-15
In terminal:

```
cat /etc/issue
```

---

### Post by clemkonan on 2006-06-15
OK but I changed the desktop to kubuntu with kde  is there still terminal or another function does this?

---

### Post by clemkonan on 2006-06-15
OK found it this is the equivalent to MS ' Help about" I sill have 5.10 Breezy Badger. however I upgraded to Dapper so what do I have to do to activate it?

---

### Post by oscar on 2006-06-15
To check/fix it open up a terminal and:
```
gksudo gedit /etc/apt/sources.list
```
you should have a file containing lots of lines like this:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
(This is just an extract from my sources.list)
If you have properly upgraded then there should be no references to breezy and only references to dapper. If it does refer to breezy for example:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ **breezy**-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ **breezy**-updates main restricted
```
Then you need to change all of your "breezy"s to "dapper"s and do a:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
The update you did could have just been an update to breezy applications, not an upgrade to dapper

---

### Post by MinkaGrl01 on 2006-06-15
I have a question also about upgrading...
I went through and did everything and then after the reboot it tells me that it "failed to start the X server (your graphical interface). It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?" after hitting 'enter' it goes to another error window 

hmmmmm, not sure what I did wrong.  But there is now an extra 23 partitions on my hdd with several  recovery modes.  Hopefully all this is easy to fix but I'm not sure how I screwed it up or how to fix it.

---

### Post by MinkaGrl01 on 2006-06-16
bttt  I really need some help, should I start my own thread?

---

