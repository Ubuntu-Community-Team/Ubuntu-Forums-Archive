---
title: "[SOLVED] Grub Question"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Wowcow on 2007-10-08
Hello, I am a noob.  There, I admitted that I have a problem.:lolflag:

I have played around with several different flavors of Linux, some with some success, others were dismal failures.  While tinkering in Gentoo, I found out how to configure Grub to change labels and default boot partitions and such.  I seem to have forgotten how to do this, as it was a few years ago that I did this.  I want to make Windows XP the OS that my rig boots into (for my wife, she isn't quite ready to take the plunge.)  I also would like to remove a few boot options (Grub seems to think that Vista is still installed and I would like to get rid of an old kernal from the boot list.)  And is it still possible to put a picture or splash of color behind the bootloader?  

Sorry for all the questions in the form of a wall of text, and in no apperant structure.  I do appreciate everyone who helps.

Thanks.

---

### Post by skymera on 2007-10-08
sudo gedit /boot/grub/menu.lst

edit out stuff you dont need.

be careful!

---

### Post by overdrank on 2007-10-08
> **Wowcow said:**
> Hello, I am a noob.  There, I admitted that I have a problem.:lolflag:

I have played around with several different flavors of Linux, some with some success, others were dismal failures.  While tinkering in Gentoo, I found out how to configure Grub to change labels and default boot partitions and such.  I seem to have forgotten how to do this, as it was a few years ago that I did this.  I want to make Windows XP the OS that my rig boots into (for my wife, she isn't quite ready to take the plunge.)  I also would like to remove a few boot options (Grub seems to think that Vista is still installed and I would like to get rid of an old kernal from the boot list.)  And is it still possible to put a picture or splash of color behind the bootloader?  

Sorry for all the questions in the form of a wall of text, and in no apperant structure.  I do appreciate everyone who helps.

Thanks.

HI this link is a great for the grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck! :)

---

