---
title: "[SOLVED] dpkg-reconfigure -phigh xserver-xorg"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-04-18
```
dpkg-reconfigure -phigh xserver-xorg 
```

This command is so helpful, it brings the GUI back whenever I screw it. I just have to login as root (recovery mode) and type this in. Just wondering if anyone could translate this command into simple English.....I want to know what does all this '**dpkg**', '**-phigh**' etc...things mean and what does this command actually do.


Thanks.

---

### Post by zvacet on 2008-04-19
dpkg =  package manager for Debian
phigh = priority high

To find out more about xserver and xorg type in terminal 

**man xserver **

**man xorg**

---

### Post by erlyrisa on 2008-04-19
It's funny how many people miss the top comments of xorg.conf

```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

```


Many a person does a fresh install just because they stuffed around with xorg.conf

---

### Post by perce on 2008-04-19
In plain English, this command reconfigures the GUI choosing the default values for almost all options, and ask the user only about options with high priority.

---

### Post by schauerlich on 2008-04-19
sudo = lets you do whatever you want
dpkg-reconfigure = reconfigures packages (similar to programs) in the debian and debian based operating systems.
phigh = priority: high
xserver-xorg = the file that stores a bunch of settings that control what the GUI looks like, among other things. Often times editing this file incorrectly makes the GUI go away, which many people would prefer didn't happen.

So, this command resets the file that controls how your GUI is displayed.

---

### Post by Google Spider on 2008-04-19
> **erlyrisa said:**
> It's funny how many people miss the top comments of xorg.conf

```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

```


Many a person does a fresh install just because they stuffed around with xorg.conf

Most of them (that includes me) have never opened the xorg.conf file.


Thanks for all the replies.

---

### Post by longboneslinger on 2008-04-19
As an extra note for those who get error messages, just change -phigh to the end of the code:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Probably an update but it gave me fits on an old lappy running xubuntu and a new(ish) dell desktop running ubuntu. Both are using 7.10 gutsy Gibbon with some folks who play with settings to much. (my wife killed the lappy and nuked my desktop myself :lolflag:)

On thing you can say in the linux vs winerz fight: If linux goes bonkers it's actually something ***_I_*** did.

Later taters,
bone

---

