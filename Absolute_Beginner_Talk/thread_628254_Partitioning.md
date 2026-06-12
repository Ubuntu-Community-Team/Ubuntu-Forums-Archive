---
title: "Partitioning"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by lwho on 2007-12-01
Hi,

I have recently installed Ubuntu on my external hard drive but now Windows won't boot on my computer.  I get the message erorr 32 when I try booting from my built in hard drive.  Any ideas on how I can make Windows run again?

Thanks,

Wayne

---

### Post by Malta paul on 2007-12-01
Hi, When you boot your computer I assume you can boot into Ubuntu?
If so the menu 'Grub' is not finding your Windows.
You may like to post a copy of 'fdisk -l' using the terminal.
Grub just needs to be set to know were your window is, I would guess it now looking on you external drive instead of you internal HD.    
Hope this helps:wink:

---

### Post by quandary on 2007-12-01
> **lwho said:**
> Hi,

I have recently installed Ubuntu on my external hard drive but now Windows won't boot on my computer.  I get the message erorr 32 when I try booting from my built in hard drive.  Any ideas on how I can make Windows run again?

Thanks,

Wayne

You installed Grub in the MBR of your built in hard drive. You have to connect your external hard drive, because some of the data to boot windows is on that disk, and then you can try to boot Windows...

read this:
[http://ubuntuforums.org/showthread.php?t=627776](http://ubuntuforums.org/showthread.php?t=627776)
and this:
[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

---

