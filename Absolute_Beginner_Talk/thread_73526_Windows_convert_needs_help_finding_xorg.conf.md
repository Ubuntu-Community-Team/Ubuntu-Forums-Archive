---
title: "Windows convert needs help finding xorg.conf"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by richpor on 2005-10-09
Greetings to all.  

like many other Windows converts, I have installed the AMD64bit version of Ubuntu on a dual booted winXp machine.  I have some experience (limited) on SCO unix boxes and have a basic understanding of some of the editors like Vi and alike.  

Here's the problem.  My system freeses just after Gnome (the GUI?) boots.  From what I have read, this is due to my RADEON X600 video card ( a common problem ).  I boot in recovery mode and try to NANO or Vi the /ECT/X11/xorg.conf file, but it's not there.  When i did the install, I installed the base system.

1.  Was I supposed to install the "Server" version, and if so, can I re-sinsall over what I have.:confused: 

2.  How can I set the GNOME to VESA mode so that I can upgrade the ATI driver.:confused: 

Any help or pointing in the right direction would be greatly appreciated.

Thanks to all in advance,

Richard

---

### Post by Perfect Storm on 2005-10-09
you have to write it exactly /etc/X11/xorg.conf 
Linux are case sensitive. There is a diffrent with eg. Dog and dog

---

### Post by richpor on 2005-10-09
[QUOTE=Artificial Intelligence]you have to write it exactly /etc/X11/xorg.conf 
Linux are case sensitive. There is a diffrent with eg. Dog and dog[/QUOTE]

The "X" in X11 must be upper case?

---

### Post by Perfect Storm on 2005-10-09
aye

---

### Post by richpor on 2005-10-09
Thanx, It worked.:D 

I shoulda remembered that from my SCO days.  Now all I gotta do is figure out the whole ATI RADEON video card thingy...

Thanx again...

[QUOTE=Artificial Intelligence]aye[/QUOTE]

---

### Post by Perfect Storm on 2005-10-09
Have you checked this?: [http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI](http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI)

---

### Post by richpor on 2005-10-09
Yes, thank you, I was going to attempt the "HOW TO RADEON DRIVERS" AfTeR I got the system up in VESA mode.

It's up now and I have downloaded all the updates.

I'll open a terminal session and try the ATI thing next.

I may be back with more questions later, but thanks for the help!!:p 

[QUOTE=Artificial Intelligence]Have you checked this?: [http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI](http://ubuntuforums.org/showthread.php?t=65276&highlight=ATI)[/QUOTE]

---

### Post by Havoc on 2005-10-09
If your xorg.conf file gets borked again, you could try "sudo dpkg-reconfigure xserver-xorg".Answer all the questions, and you're good to go!

---

