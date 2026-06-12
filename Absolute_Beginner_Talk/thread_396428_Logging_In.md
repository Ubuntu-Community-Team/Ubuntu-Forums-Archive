---
title: "Logging In?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Benjamin Poulton on 2007-03-29
I have installed Ubuntu 6.10 on my laptop. During the installation I was prompted to enter a password, which I did, but was never asked to provide a username. After the installation, Ubuntu prompted me for a username at the login page, but I have not created one. How do I find out what my username is?

---

### Post by tiendn on 2007-03-29
I have got problem like u, U try to reinstall Ubuntu with text mode.

---

### Post by mcduck on 2007-03-29
I bet you used the OEM install instead of normal one? Next time don't do it, it's only needed if you want to sell computers with Ubuntu preinstalled.

Anyway, here's how to finish the OEM install and get to the real thing:

First, log in using the username 'oem' and the password you made when during the install. Then open a terminal and run 'sudo oem-config-prepare' and use the same password. This will finish the installation and remove the OEM user. Then boot the machine, and now Ubuntu will ask you to create the actual user for the machine.

The idea in OEM install is that you can install Ubuntu, do some extra configurations like installing codecs and extra software, and then run the 'sudo oem-config-prepare'-command to make the computer ready to be shipped to the customer. Then when the customer boots the machine first time  the real user is created, just like when you buy a computer with preinstalled Windows.

It's not any use for home users, as Ubuntu is already free so you won't get the benefit of cheaper price which is the main reason why people get OEM install disks for Windows.

---

