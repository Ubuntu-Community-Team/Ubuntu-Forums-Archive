---
title: "It  can just see 1 XP pro"
date: 2012-07-14
forum: Any Other OS
---

### Post by m10sang10 on 2012-07-14
Gentlemen;

I have a problem with Ubuntu 12.04' Grub, my PC boot a few O.S 
from some HDs. Two of my OS are XP-PRO (yes, I know it sound illogical...but) and I want that to continue so.

With Grub legacy I had no problems at all and before that Grub 2 another versions let me modify manually: 
gksudo gedit /boot/grub/grub.cfg for: 
drivemap (hd1) (hd0)
 drivemap (hd0) (hd1) 
+ stop grub update.

I installed the last Ubuntu and although it seemed to recognize the OSs' it just can see 1 XP pro, and even though I can modify manually the grub, when restarting, its rewritten to the initial state (no modification at all). 

Perhaps you could help me.
Thanks in advance.

PD: XP home and XP Pro will work?

---

### Post by mwl128340 on 2012-07-14
to get any help on this issue, you may want to give a little more info about your system. running a bootinfoscript is a good place to start. and post the results in your post.(just dont forget to wrap the results in your post, it is a long output with alot of information) here is the link to download the file and the instructions to run it are included in the file.[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by oldfred on 2012-07-14
Moved to Other OS.

+1 on bootinfoscript.

You do not edit grub.cfg but if you do want custom entries add them to 40_custom.

To understand how Windows boots:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

