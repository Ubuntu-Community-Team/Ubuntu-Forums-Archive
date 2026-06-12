---
title: "How to enable direct rendering?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by nocnashada on 2008-04-08
I am running XUbuntu on HP Compaq 6710b, which has an integrated graphics card X3100.

Now my problem is enabling direct rendering. I already have the xserver-xorg-video-intel package installed and xorg.conf has "intel" for driver. Asked a few of my friends what to do and none of them were able to help me so far...

additionally eclipse is asking for glx to be updated from 1.2 to at least 1.3, maybe these wo are connected somehow...

Thanks in advance...

---

### Post by ubuntu-freak on 2008-04-08
As far as I know it should be enabled by default, but it's blacklisted in regard to Compiz Fusion. Have you tried reconfiguring the xserver?
 
**sudo dpkg-reconfigure -phigh xserver-xorg** 

Just so you know, in Debian I was told DRI was disabled, when it actual fact it was enabled.  Are you sure it's disabled? 
 
Nathan

---

### Post by nocnashada on 2008-04-08
Nope, still doesn't show "Yes"...
I'm pretty sure it doesn't work yes... at least as far as anything graphical goes, the computer is abyssmally slow(tests made on a few simple games, and general responsiveness of x server).

---

### Post by ubuntu-freak on 2008-04-08
> **nocnashada said:**
> Nope, still doesn't show "Yes"...
I'm pretty sure it doesn't work yes... at least as far as anything graphical goes, the computer is abyssmally slow(tests made on a few simple games, and general responsiveness of x server).

 
Does it work when using "i810" instead of "intel"? 
 
Nathan

---

### Post by nocnashada on 2008-04-08
That doesn't work either....when i restarted the x server the screen flickered a few times, while it was trying to run dunno which script then threw me into "low graphics".
I have xserver-xorg-video-i810 installed....

---

### Post by ubuntu-freak on 2008-04-08
I'm pretty stumped, sorry.
 
Have a look at the following site and see if anything helps, espectially the xorg.conf details:
 
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)
 
Nathan

---

### Post by nocnashada on 2008-04-09
Thanks, I'll check it out.

---

