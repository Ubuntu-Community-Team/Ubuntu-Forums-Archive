---
title: "Apollon install"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-07
I want to install Apollon on Xubuntu, but when  I tried what the howto installl guide said ([http://www.ubuntuforums.org/showthread.php?t=59857&highlight=apollon+install](http://www.ubuntuforums.org/showthread.php?t=59857&highlight=apollon+install)) I had problems, the problem was this: 
```
jorge@ubuntu:~$ sudo apt-get install gift giftd apollon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gift

```
What do I have to do to install it on Xubuntu 6.10? 
Can anyone help me please?:confused:

---

### Post by taurus on 2007-01-07
Did you enable both universe & multiverse in /etc/apt/sources.list?  If you haven't, try to remove the # in front of all the lines that have universe or multiverse in them (with deb at the beginning).  Then see if you can install gift again.

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get install gift giftd apollon
```

---

