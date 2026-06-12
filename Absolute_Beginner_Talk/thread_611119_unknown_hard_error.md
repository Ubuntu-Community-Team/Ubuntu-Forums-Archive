---
title: "unknown hard error"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-11-12
hi , i am dual booting ubuntu 7.04 and xp , i was watching movie on xp , suddenly i got a unknown hard error , movie was automatically closed and when i opened my computer , there we no drives in it and i was unable to restart , so i reset it , then i again tried to start windows and now windows wont start in both normal and safe mode , thank god i had linux and its working totally fine , atleast i can complete my movie , lol .
i can see my all drives in ubuntu , so is there any way i can scan drive in which windows is installed through ubuntu , i mean check that drive for any bad sectors or errors.

---

### Post by houstonbofh on 2007-11-12
There are ways...  You can mount the drive automatically.  However, to fix windows it is hard to beat the UBCD4win.  [http://www.ubcd4win.com/](http://www.ubcd4win.com/)  The catch is that you need to build it on a working windows system.

---

### Post by damansandhu on 2007-11-12
man , my windows is not working , i need to do something in ubuntu

---

### Post by houstonbofh on 2007-11-13
OK.  You need Gutsy.  In Feisty it works, but is difficult.  In Gutsy, you have to manually mount, but it is read/write by default.  Get a Gutsy Live CD, and boot.  Got to Places --> Computer.  You should see you disk labeled something like '92.3 GB Volume' but the size of your drive.  Right click and mount.  If that fails, (I am not on a Live CD right now) you may have to do it with a root file manager.  Open a CLI and type 'sudo nautilau --no-desktop' and you will have a root file manager.  Try again.  If that fails, you may need to build a mountlist.

Or, you can patch your Ubuntu system like this. [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite) However, I am not sure what will happen on an upgrade.  You may want to back out the changes before going to Gutsy.

Or, Go to Gutsy and hope you don't hose both systems at once. :)

---

