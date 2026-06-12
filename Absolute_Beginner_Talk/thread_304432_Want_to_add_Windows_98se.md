---
title: "Want to add Windows 98se"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-11-21
I am running Ubuntu as my only operating system.  I want to add back on Windows 98se so I can run some old programs.  I need no Internet access with this installation. How do I go about reloading grub so I can dual boot the system.

---

### Post by turbojugend_gr on 2006-11-21
I suggest you not to do this, as windows will wipe out GRUB. You should try to run this programs via wine, especially if they are old apps it is more likely they can be run through wine.

Another choice would be VMWARE. Finally you could learn how to install grub and configure it fpr your self, and then install win98 and instal-then-configure grub accordingly.

Cheers, TJ.

---

### Post by ReaderRat on 2006-11-21
Take a look at the [[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto) And at this;
Restore GRUB after installing Win
          **[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)**

---

### Post by snype on 2006-11-21
This is a little different from what you're asking to do, but have you thought about using the program WINE? It is by no means a dual boot, but it will allow you to run many windows programs in ubuntu! A lot of programs do not work, or take a bit of effort to get them to work, but in my experience older programs, ie ones targeted at windows 98 actually work the best. Just a thought. I'd advise using the suggestion above if you absolutely must install windows alongside ubuntu, but becareful because I'm pretty sure that windows will wipe out you're linux install if you dont resize the partition and format it to Fat 32. Have you looked for open source alternitive's to the software you want to run? I.E Open-Office instead of M.S. Office or GIMP instead of Photoshop? Just some ideas. Good Luck.
-snype

---

### Post by LLRNR on 2006-11-21
Before messing up GRUB you could try Wine like others suggested. I think [this](http://doc.gwos.org/index.php/HowToWine) might come in hand... Good luck ! ;)

LLRNR

PS - What are those apps you need, by the way? Maybe there are equivalents already, who knows ?

---

### Post by louieb on 2006-11-21
Surefire way? See my [Post]("http://www.ubuntuforums.org/showthread.php?p=1777410#post1777410") on this subject.

---

### Post by alienexplorers on 2006-11-22
Got it working with no problems since I am running from Windows right now.  Ran gparted, added windows, ran live cd to edit grub and away I was running Linux and Windows.  This was really easy.

---

