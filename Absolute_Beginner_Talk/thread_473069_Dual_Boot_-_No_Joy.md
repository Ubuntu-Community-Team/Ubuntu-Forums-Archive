---
title: "Dual Boot - No Joy"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by shadds on 2007-06-13
I have just installed ubuntu 7.04 (dual-boot) with windows vista yet i have the following problem.
when i boot up ubuntu from the GRUB loader it gets to what i belive is the main screen a beige colour with a ubuntu logo in the middle. apart from this there is a grey box in the top left corner but nothing else. it seems that the system just hangs any ideas?

---

### Post by locke.dragon on 2007-06-13
did you try running the live cd first?  and if so, did it work properly?

---

### Post by shadds on 2007-06-13
the live cd seemed to work fine... well the desktop looked as it should e.g the desktop had a taskbar and there were icons but to be honest i ddint went straight to the install.

---

### Post by locke.dragon on 2007-06-13
were there any "hiccups" in the install?  such as periods where the computer didn't seem to be doing anything?

---

### Post by shadds on 2007-06-13
After the install when i rebooted the computer checked something what i assumed was the hard drive as it said it hadn't been checked for 49000 days!! so the check was forced. i didnt think anything of it though is it important?

---

### Post by ryanVickers on 2007-06-13
Sounds like it's not detecting things properly.  It will usually auto-check every 20 to 30 boots, but that period of time works out to ~134 years, so something is not quite right! :p

---

### Post by shadds on 2007-06-13
is it possible to repair the install from the disk like is possible in windows?

---

### Post by ryanVickers on 2007-06-13
Yes, except I think it is better!  the windows check disk just says (and I'm not kidding!):
checking or fixing some files
checking or fixing some more files
checking or fixing some more files
checking or fixing some more files
1 or more files were checked and fixed
:lolflag:

Where as in ubuntu, you can do a check disk command on the file system in the terminal like this:
```
cfdisk /dev/%DEVICENAME%
```

---

### Post by locke.dragon on 2007-06-13
naw.  don't worry about the 4900 days thing.  that's just a bug in feisty.  there's a thread on here somewhere about it, but i'm feeling too lazy to find it.  :P  were there any other problems?

---

### Post by ryanVickers on 2007-06-13
Is it just the GDM perhaps?  Have you tryed booting in recovery mode and loggin on as root from the command line?  If from there everything is ok, then that would prove it!  Oh, if you try it, then once logged on, you have to go "startx".

---

