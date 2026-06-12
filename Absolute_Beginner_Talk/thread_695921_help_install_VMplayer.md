---
title: "help install VMplayer"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-13
im using gusty and ive downloaded the Zar file a few time and everytime i try the command

VMware-player-2.0.2-59824.i386.tar.gz

i get this

tar xzvf VMware-player-2.0.2-59824.i386.tar.gz
tar: VMware-player-2.0.2-59824.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kyle@kyle-laptop-Ubuntu:~$

what can i do ive tried a few different tutorials but all make u do this step and i cant 

and ive right clicked and excract here and it didnt do anything

---

### Post by Thelasko on 2008-02-13
Check to see if it's in the repositories before you install it this way.

Applications>add/remove programs

I had to install it from the tar.gz myself.  Here is what you are doing wrong:

You need to point your terminal to the directory the file is in.

Example:
```
cd /home/username/desktop/
```
Note: replace username with your user name and this assumes you have the file on your desktop.

Hope that helps!

---

### Post by profediego on 2008-02-13
have you try 

sudo apt-get install vmware-player

make sure you have all the repositories enabled.

---

