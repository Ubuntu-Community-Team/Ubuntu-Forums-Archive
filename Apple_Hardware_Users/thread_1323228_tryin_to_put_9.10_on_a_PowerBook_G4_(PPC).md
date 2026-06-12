---
title: "tryin to put 9.10 on a PowerBook G4 (PPC)"
date: 2009-11-11
forum: Apple Hardware Users
---

### Post by ant2ne on 2009-11-11
I'm using the alternate CD and booting with install video=ofonly At about 85% of the Select and install software step

> An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software <continue>Continue takes me back to the menue. with that step highlighted. Executing a shell and doing a dmesg shows the final entry
```
[234.414668] JBD: barrier-based sync failed on hdsa3:8 - disabling barriers
```I don't know what that means. I don't know if it is related. Nothing else on dmesg looks error related
dmesg | grep fail shows only the above mentioned entry.
dmesg | grep error shows nothing

If I execute the step again, it does continue and seems to intall the OS reboots. Of course, it reboots, I get an 8 bit ubuntu logo. And then a black screen forever. Pressing Alt + Cntl + F1 doesn't get me to a prompt either. Just a black screen.

---

### Post by ant2ne on 2009-11-11
```
Linux video=ofonly no splash
```Still get the black screen```
Linux single video=ofonly nospalsh
```got me to a menu. Which to me means, the system is booting. I couldn't get to a shell because i go the bug > give root password for maintenance or type control-d to continue(yes it is a bug, why have it if you can't do it. This should be fixed to allow sudoer acces to maintenance.)
From this menu I could select repair broken packages. Which I did select and it is currently running. I'm getting a lot of ```
preparing to replace(package name).... .../(package name)/2.28.1-0ubuntu2_powerpc.deb) ...
```so maybe whatever didn't pooped on "An installation step failed." will get fixed.

---

### Post by Dark_Ronius on 2010-01-09
Having the same problem on my iMac G3... although interestingly when I continue from the step and reboot the system, it still has the 8-bit look you've described, but it also shows the gui login screen. However none of the users I have set up can log in, as if they don't exist.

On a side note, which Ubuntu would you suggest is the best to use with the mac? Inherited it off a friend (without a mac os disc) and just wanted a replacement for the sluggish Mac OS X that was already installed.

---

### Post by linuxopjemac on 2010-01-10
Ubuntu/PPC is not a great option. I can recommend Debian Lenny/PPC.

---

