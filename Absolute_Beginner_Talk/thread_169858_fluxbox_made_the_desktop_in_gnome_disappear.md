---
title: "fluxbox made the desktop in gnome disappear"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-05-03
I'm using breezy badger with the gnome display manager. Someone told me about fluxbox and i thus installed it to see how fast it works. It was rather impressing, but since i do not only want to get to know the computer programs, but am also willing to use the machine to do some work stuff, i'd like to  be able to switch to gnome back, where i know how thinks sort out. I managed to switch to gnome back, but now found that neither the desktop background (which is unimportant to me, but may be a usefull information to you) nor the icons appeared on the desktop. all the other things work fine. How can i get my desktop back?

Can you furthermore explain me what the difference between xserver gnomedisplaymanager gnomewindowmanager and fluxbox is? I mean is there a kind of hierarchy where the one stands above the other? Thanks, niko

---

### Post by NetMatrix on 2006-05-03
Niko,

Xserver is at the top of the list, none of the other window managers can run without it.  However it by itself is not enough, another piece call the x-windows-system-core is also required.  To my knowledge gwm and fluxbox are on the same level and gdm is for graphical login.  As for your first question I cannot help, but there are IRC channels for fluxbox maybe you can find help there.

---

### Post by gagatz on 2006-05-03
Thank you, but i still don't know how to get the symbols back. How can I do it?

---

### Post by annda on 2006-05-03
do you have any icons on your desktop? drives/partitions have disappeared too or only your "shortcuts"?

I don't know what happened but more details would help us do some research.

if you add a file to your Desktop directory (via GUI i.e. right-click and create new file or by moving a file to your home/username/Desktop dir), does it appear on the desktop?

---

### Post by gagatz on 2006-05-03
Normally on the Desktop are two mounted harddrives,  some pdf docs and some links to other directories. None of them are visible, and if I rightclick, nothing happens. It is also not possible to draw a frame. Some sessions earlier gnome warned that HAL hasn't been loading, but in the current session and the last three before it didn't warn. Furthermore I selected the gnome display manager at the login screen selection possibility. Actually the install of fluxbox took quite a lot of time. The computer was working hard to get all the files working, while I could see, that while performing the requested operation in a terminal, some different errormessages appeared, but since fluxbox works fine, i don't regard them as important. Anyhow I don't believe they have something to do with the gnome thing. If it is of interest for you and you tell me where the log files are, i can post the error messages here. To install fluxbox I followed the guide of [otake-tux]("http://ubuntuforums.org/showthread.php?t=116759")

---

### Post by NetMatrix on 2006-05-04
I'm not sure if this will work. But I would like to see if Metacity is running.

I think

```
ps -AF |grep metacity
```

will find it.

---

