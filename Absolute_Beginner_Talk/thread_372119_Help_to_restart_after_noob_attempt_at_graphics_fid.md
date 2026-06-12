---
title: "Help to restart after noob attempt at graphics fiddling"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-02-27
Well, I had no problems partitioning my XP drive and getting Ubuntu onto my PC.  I downloaded an Nvidia driver through an application getter that I had downloaded and all was working well............
Problem is my Nvidia Geforce 7600 gs card settings werent being recognised.  I was stuck with the default.  I have an Asus VW192S monitor that is 19" widescreen capable of 1440X900.
I looked on these forums and managed to access the xconfig something or rather whatnot and cut and pasted a load of bits and pieces from other posts:)   I tried to restart and BAM!  Nice new OS down the pan:confused: 

1.  Can anyone help me get past the blue graphical interface failure bit.  I have worked out how to add lines (I am that new to this) and tried sudo dpkg_reconfigure xserver-xorg but this wasn't recognised.

2.  Once i have it up and running can anyone suggest a driver and location.  There is all sorts of stuff out there and as you can tell I am clueless:lolflag:

---

### Post by igknighted on 2007-02-27
To get your GUI back, run this command in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
pick the nv driver, and defaults for most things.  In fact, you might get your res back here.  If you want 3d graphics enabled, try downloading the "envy" script (the italian word for envy sounds like nvidia, its a play on words/languages).  This will install the official nvidia drivers for your system.

---

### Post by Roger_Melly on 2007-02-27
Cheers, I shall try post haste....it's getting rather late/early!?!

---

### Post by Roger_Melly on 2007-02-27
Thanks igknighted,
I am back up and running.  I was too much of a Klutz to know how to mark the 1440x900 box so I'm back to square one!  It's not such a bad place.  Can I enter these setting once in the GUI?
How do I mark the BIOS looking boxes (I tried the *)?
And where can I find envy?  It isn't in my SPM.

---

### Post by Roger_Melly on 2007-02-27
Fantastic.................................:guitar: 
managed to get Envy to work and after a bit of fumbling (don't miss the black screen hint Alt-F1) and away it went.
Hey presto I can hardly see my writing now!
Many thanks

---

### Post by Maestro23 on 2007-02-27
> **Roger_Melly said:**
> Thanks igknighted,
I am back up and running.  I was too much of a Klutz to know how to mark the 1440x900 box so I'm back to square one!  It's not such a bad place.  Can I enter these setting once in the GUI?
How do I mark the BIOS looking boxes (I tried the *)?
And where can I find envy?  It isn't in my SPM.

Envy: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

