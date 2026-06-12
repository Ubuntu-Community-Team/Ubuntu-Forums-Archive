---
title: "can not install Ubuntu or Kubuntu"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by electrodad on 2007-01-13
I was running Ubuntu 6.10  /XP pro  dual boot  on my Dell laptop fine. I even had my Firefox flashplayer plugin working. I was attempting to burn a DVD iso. It kept hanging up, I'm not sure what happen after that, but the Bug window started popping up after that I tried saving and closing it but it kept coming back. Finally in my nOOb wisdom I decided to reinstall the system. I booted to the CD and attempted to install Ubuntu again, but every time I try  I get a line  that read something about bug: locked CPU 0 something. At this point I run a PCLinux  install disk which is what I'm using as of now. Every time in the past I've been able to install Ubuntu after the PCLinux and get Ubuntu back, but not anymore.What's has happened?:confused:

---

### Post by floke on 2007-01-13
How do you reinstall? Is it just telling Ubuntu to write over the existing Edgy? If so, you could try deleting the edgy partition along with the swap file and reinstaling using the 'use largest available free space' option?

---

### Post by Threbus5 on 2007-01-13
You were previously able to reinstall Ubuntu and it corrected corrupted/altered files while retaining your other configurations? Wow. 

Can you use your backup to revert to the pre-disaster condition? 

You could reinstall into the largest available free space, then choose that installation as the one you start from during boot choices.

Best Wishes

---

### Post by BarfBag on 2007-01-13
Delete the root and swap partitions through Windows.  Then, when you get to the partitioning section of the Ubuntu setup, choose the "Install to Largest Contiguous Space" option.  This is what I do whenever I have to reinstall Ubuntu.

To delete the partitions (in Windows XP): Start -> Control Panel -> Administrative Tools -> Disk Management.  There's a tab (forget what it's called) that has your partitions in it.  Just right click on the ones you want to delete, and hit "Delete."

---

### Post by electrodad on 2007-01-16
> **BarfBag said:**
> Delete the root and swap partitions through Windows.  Then, when you get to the partitioning section of the Ubuntu setup, choose the "Install to Largest Contiguous Space" option.  This is what I do whenever I have to reinstall Ubuntu.

To delete the partitions (in Windows XP): Start -> Control Panel -> Administrative Tools -> Disk Management.  There's a tab (forget what it's called) that has your partitions in it.  Just right click on the ones you want to delete, and hit "Delete."

I tried disk manager as well as another program called Super Fdisk, but still no go. I tried installing Kubuntu this morning before leaving for work, here's the message I recived.

"[17179701,360000] BUG: Soft lockup detected on CPU#0" 

Just about every time weather I try Ubuntu or Kubuntu still the same results](*,) . This is very fustrating. Anyone have any ideas what might of happened.

---

### Post by phr0ze on 2007-01-16
Did you try the memory test from the live CD? maybe your hardware is having problems. I like to blame the PSU before the Ram though.

---

### Post by electrodad on 2007-01-17
> **phr0ze said:**
> Did you try the memory test from the live CD? maybe your hardware is having problems. I like to blame the PSU before the Ram though.

Well the RAM test was fine and I still have the same issue, but it is only with Ubuntu Distro the other distro of linux do not have a problem. What could have changed?:-k  I have reloaded Ubuntu before over another distro of Linux.

---

