---
title: "Path/folder issues in Wine"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-10-16
Hi,
I'm not even sure whether this is the right place to ask the question - if it isn't, feel free to point me in the right direction! - but I just tried to install a Windows 3D modeling program in Wine and it wouldn't run the install.  Here's what Terminal told me:
> / wine ~/Desktop/DazStudio1719.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/robyn', starting in the Windows directory.
wine: cannot find '/home/robyn/Desktop/DazStudio1719.exe'

I keep seeing this error... I have no idea what L"c:\\windows" is, or how to edit this. None of this shows in tha multi-tab thingie that comes up when you issue a winecfg in Terminal.  I'm running Ubuntu 7.04 and Wine .9.47, which reportedly is able to install and run the program in question: DazStudio.
Thanks in advance.

---

### Post by Dr Small on 2007-10-16
Try moving the exe into ~/.wine somewhere (I forget, I don't have wine installed).
It should be something like ~/.wine/c/program files or something.

Then try running the exe with wine.

Dr Small

---

### Post by Kilz on 2007-10-16
> **Robynsveil said:**
> Hi,
I'm not even sure whether this is the right place to ask the question - if it isn't, feel free to point me in the right direction! - but I just tried to install a Windows 3D modeling program in Wine and it wouldn't run the install.  Here's what Terminal told me:

I keep seeing this error... I have no idea what L"c:\\windows" is, or how to edit this. None of this shows in tha multi-tab thingie that comes up when you issue a winecfg in Terminal.  I'm running Ubuntu 7.04 and Wine .9.47, which reportedly is able to install and run the program in question: DazStudio.
Thanks in advance.

[You may want to look for answers in the wine application database.]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1998")

---

