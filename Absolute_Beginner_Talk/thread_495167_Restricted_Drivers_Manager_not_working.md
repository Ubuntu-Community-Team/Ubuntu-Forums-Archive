---
title: "Restricted Drivers Manager not working"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by FRanzH on 2007-07-07
Hi!

Ive just tried to make the wireless work on my macbook that i set up dualbooting with ubuntu on and a pop up came up saying about restricted drivers manager.
Now im new to linux and have only been using it for a few days but when i go to open the Restricted Drivers Manager it says that i need to install it but i have no idea how.

Can someone pelase guide me onto how to get it to work?

Thanks!
Franz

---

### Post by Vague on 2007-07-07
It's telling you that you need to install the Restricted Drivers Manager?  That seems odd.  Anyway, assuming you've got a Core 2 Duo MacBook, this will probably help: [http://ubuntuforums.org/showthread.php?t=429641](http://ubuntuforums.org/showthread.php?t=429641)

---

### Post by originald on 2007-07-07
Do you mean you need to install the Restricted Drivers Manager ?

If so type these commands into a terminal window

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

Then you can access the Restricted Drivers Manager from System > Administration > Restricted Drivers Manager

---

### Post by FRanzH on 2007-07-07
Well i just tried out the link and some of the things dont work for me, and i just tried thoes two lines of code but it says i wallready have the latest version.

Ill add mroe info: it says 

You need to install the package

  linux-restricted-modules-2.6.20-16-lowlatency

for this program to work.


Thanks

---

### Post by FRanzH on 2007-07-07
just installed it via the package manager - sorry it was just me being new :)

---

### Post by Vague on 2007-07-07
> **FRanzH said:**
> Well i just tried out the link and some of the things dont work for me, and i just tried thoes two lines of code but it says i wallready have the latest version.

Ill add mroe info: it says 

You need to install the package

  linux-restricted-modules-2.6.20-16-lowlatency

for this program to work.


Thanks

Try typing this in the terminal: ```
sudo apt-get install linux-restricted-modules-2.6.20-16-lowlatency 
``` and see if that works.

Edit: Didn't see your last post before I made this one.  Congrats on getting it.

---

### Post by FRanzH on 2007-07-07
Hey vague - that link you gave me, well the links in the code are outdated and dont exist :( sorry that this is off topic from the threads title

---

### Post by Vague on 2007-07-07
Woops, sorry.  I was pretty sure they'd still be good, since that's only a few months old, but I guess I was wrong.

---

### Post by FRanzH on 2007-07-07
Ok well thanks anyway :)

Much apreciated

---

