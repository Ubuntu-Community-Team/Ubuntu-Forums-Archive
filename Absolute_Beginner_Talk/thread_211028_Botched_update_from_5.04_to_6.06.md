---
title: "Botched update from 5.04 to 6.06"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Newby on 2006-07-07
](*,)
[I hope this is in the correct part of the forum.]
  I am completely new to Ububtu and ignorant of Linux. 
Yesterday, I installed Ubuntu 5.04 on my PC's 2nd hard drive. Worked perfectly, went without a hitch, ran beautifully. But then I discovered that there was an Ubuntu 6.06 out there. So, I downloaded the Ubuntu 6.06-server i386 ISO on my iBook and burned it. I slipped that installation CD into my PC and installed that on the same hard drive that 5.04 had been on, letting it overwrite everything on that hard drive. [I have no docs to save in Ubuntu 5.04.]

After a remarkably short period of installation time, it came to what I assume is a terminal screen, and it waited for me to give a command. [I don't know Linux commands.] So, I'm stuck. Is installation incomplete? What do I do at the command prompt to get the desktop screen? I just want a clean install of 6.06.

Newby :mrgreen:

---

### Post by bruce89 on 2006-07-07
The server version is not the one that you want.  You'll have to install the normal version.  If your internet connection works, then type this ```
sudo aptitude install ubuntu-desktop
```
It would be better to just reinstall Ubuntu again though, as the server one has loads of server programs installed.

---

### Post by klytu on 2006-07-07
> **Newby said:**
> ](*,)
[I hope this is in the correct part of the forum.]
  I am completely new to Ububtu and ignorant of Linux..... So, I downloaded the Ubuntu 6.06-server i386 ISO on my iBook and burned it. Newby :mrgreen:

This forum should be an excellent place to get help with this. It appears you have installed a server installation; probably you want a desktop installation. Try downloading the alternate-install ISO or the desktop ISO and install from one of those. 

If you actually wanted a server installation, another forum member should be able to help you out. I have never done one of those installations.

---

