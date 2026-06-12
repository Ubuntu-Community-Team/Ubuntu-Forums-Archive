---
title: "How to set-up Windows Dual Boot"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by HenningS on 2007-05-15
Well, I have this old PC running Ubuntu Feisty. Now I want to install XP on it, so that I can choose at startup which OS I want to use. How do I do this?

---

### Post by lazyart on 2007-05-15
There are dozens of howtos on this, but the nitty gritty of it is that you have to install windows first, then ubuntu.  When installing win don't use the whole drive as a single partition as you'll need a seperate space for linux.  If you want to share data its best to leave a fat32 partition as both OS can use it without effort.

Search for HOWTO dual boot.  Your question has been covered already.

---

### Post by rich.bradshaw on 2007-05-15
You don't if you want it to be easy.

Easiest way is to install Windows first, then Linux. Windows won't boot unless it is the first partition AFAIK, plus Windows will replace MBR, so you will have to manually install grub.

If you still want to, do this.

Backup your /home dir. 

Install Windows, give it as much drive as you fancy, make sure you manually partion. Delete whole disk, then partition a bit for Windows, maybe 5GB or something.

Install Windows, and get annoyed with all the dialog boxes etc.

Reboot 500 times till it's installed.

Boot into Ubuntu

Install on the other part of disk. Put your /home on a seperate partition for ease of future upgrading.
Give yourself same swap as Ram if you want to hibernate.

That's it.

If you install Windows after Linux it's complex, not even sure if it will work.

---

### Post by HenningS on 2007-05-15
Well, I suppose I could install Windows and then install Linux. Life is hard, eh? :( 
Anyway, thanks for helping, I'll let you know how it goes.

---

### Post by PetruM on 2007-05-15
Hi HenningS,

I've ran into that problem too and that's just because Windows won't ask before it changes the MBR and it treats ext2/3 filesystems as unknown. So, you can find a solution **[here]("http://www.linuxquestions.org/questions/showthread.php?t=478809")**. Read post **#4**, it worked every time for me. Good luck. ;)

---

