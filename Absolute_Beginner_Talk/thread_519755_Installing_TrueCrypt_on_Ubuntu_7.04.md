---
title: "Installing TrueCrypt on Ubuntu 7.04"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-07
I've always used Truecrypt to encrypt financial data on my Windows Machine and was
curious if I could do the same with Ubuntu 7.04

I'm new to Linux so I'm not sure how to install it.
I searched for it in the install / uninstall program that Ubuntu offers but didn't see it.
I even changed the settings to all open source projects.

I like all things tech and am willing to learn Linux in order not to move to Vista.
(  I just am feed up with Windows and would like to learn something different )

I'm trying to move into a new OS and get everything set up like my Windows Machine.
As soon as I have it set up the way I like it, I think I'll be very happy.
So far I really like the OS.

I'm currently Running it on Virtual Box and it seems to do well.
I want to get familiar with it before the big format.
I may even duel boot, we'll see.

Thanks for you help.

---

### Post by splintercellguy on 2007-08-07
Have you tried this guide? [http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

---

### Post by Orbital75 on 2007-08-07
I looked through it on a search I did but wasn't sure if it would work with Ubuntu 7.04
Just wanted someone to say that process worked before I mess something up..... 
I'm new to all this linux stuff and if I break something I won't know how to fix it.

---

### Post by onestep on 2007-08-07
I'm looking for the same solution as you are Orbital75. I'm new to Linux Ubuntu (again), really like what I see this time, and would love to find a TrueCrypt solution / equivalent.

On the TrueCrypt site they offer for download a ".tar.gz containing a .deb or .rpm package" specifically for  Ubuntu 7.04 x86. I'm not sure how to install or configure it though. You can find it here: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

From what I've been able to Google, I'm not sure there is a GUI version yet. All I've found is lot's of talk about running it from the command line...

I've subscribed to this thread. Hopefully someone can point us in the right direction.

---

### Post by perarild on 2007-08-09
Truecrypt is only terminal, no gui for linux.


To install: sudo apt-get install truecrypt

[EDIT] Noticed that truecrypt is not in the ubuntu package system, so you will need to download it. Download, then simply double click the .deb and the package installer will do the rest for you. [/EDIT]

To use: type "truecrypt -help" in terminal and you get a list of available commands and what they do. Normally you would type as follows to mount a tc volume:

truecrypt -u /user/tcfile /media/tc

Where

[-u] is to determine that it is a user mount, meaning it will be accessible to non administrators.
[/user/tcfile] is the path to the encrypted file you want to mount.
[/media/tc] is the path to where you want to mount your encrypted volume.
Make sure this path exists before you mount.

Hope this helps.

---

