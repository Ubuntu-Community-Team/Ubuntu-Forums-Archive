---
title: "Ubuntu w/ Crashed Desktop"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by mroark on 2006-03-06
Hello to all the Ubuntu people and many thanks to all who help us noobs out!  I got Ubuntu installed using bare minimum, however upon trying to change the screen size and resolution I crashed the desktop.  I followed up on previous post to use DSL or Ubuntu Lite with xfce4.  I don't exactly know which of these allow me to make it, so I'm glad for the crash to understand what I have done.  Using a sudo command (I don't have with me at work) I was able to get to commands that allowed me to change screen and resolution.  The command line was something like: sudo _______ change.resolution xserver.xorg  Is there any way to correct this.  I get messages saying I have errors and that gnome can't be found.  I had Ubuntu working with full install, but was too slow to use.  This is why I'm working on a lighter version.  My specs: P3 500 Mhz, 64Mb Ram, w/integrated video.  Again any commands that might restore desktop?  Thanks ahead!:-D

---

### Post by IYY on 2006-03-06
Well, if want you want to do is reconfigure you X server, you'd want this:

[INDENT]**sudo dpkg-reconfigure xserver-xorg**[/INDENT]

If you want to get XFCE, you should use:

[INDENT]**sudo apt-get install xubuntu-desktop**[/INDENT]

This will install XFCE4, AbiWord and some other stuff.

---

### Post by mroark on 2006-03-06
[QUOTE=IYY]Well, if want you want to do is reconfigure you X server, you'd want this:

[INDENT]**sudo dpkg-reconfigure xserver-xorg**[/INDENT]

If you want to get XFCE, you should use:

[INDENT]**sudo apt-get install xubuntu-desktop**[/INDENT]

This will install XFCE4, AbiWord and some other stuff.[/QUOTE]


Thanks... I'll give it a try!  I'll probably format and start over.

---

