---
title: "help-wireless lan w200"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Anthony0857 on 2008-03-29
I installed Ubuntu v.7.1 this morning on my laptop, a Compaq Evo N610c.  I usually connect to the internet on my laptop with a wireless card, the Wireless LAN W200.  I've been trying to get this wireless card to work, and I tried to follow the instructions at [https://help.ubuntu.com/community/WifiDocs/Device/%20CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/%20CompaqW200) , but I'm having some problems. 

 It asks me to install several packages with the command line, but when I run the text posted that is supposed to install them all at once, there are errors, and it doesn't install them all.  When I tried installing them individually, I found that the ones that weren't installing were subversion, curl, gcc-3.4, and cpp-3.4, and they all say
 
E: Couldn't find package 'package name here',

 except for curl, which says,

 Package curl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package curl has no installation candidate

I've looked, but I can't figure out an alternate way to install these things.  Can anyone help me figure out how to install them?

---

### Post by Anthony0857 on 2008-03-29
Never mind, I found Synaptic package manager, and was able to get the packages I needed.  Once I did that, I was able to set up the wireless card without much difficulty, and now it works.

---

