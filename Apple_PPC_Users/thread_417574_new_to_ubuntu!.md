---
title: "new to ubuntu!"
date: 2007-04-21
forum: Apple PPC Users
---

### Post by halfmexicanojcv on 2007-04-21
hello all,
can anyone explain a procedure for booting ubuntu from an external hard drive?  i'm currently downloading the iso after hearing cool stuff from my roommates about ubuntu and beryl.  i have a 1.4 ghz g4 ibook with 1gb memory.  i am hesitant to mess with my current set up until i get familiarized with it first.  is this do-able?  :) 
thanks!

---

### Post by scrooge_74 on 2007-04-21
Are you downloading the MAC version? That is important.  You will be able to install to an external drive, but you need to either tell your BIOS to boot from there or install GRUB to your first drive so Ubuntu can let you dual boot.


You should first use the Live CD for a  while so you can get familiar with the system, welcome aboard

---

### Post by rccharles on 2007-04-21
> **halfmexicanojcv said:**
> hello all,
can anyone explain a procedure for booting ubuntu from an external hard drive?  i'm currently downloading the iso after hearing cool stuff from my roommates about ubuntu and beryl.  i have a 1.4 ghz g4 ibook with 1gb memory.  i am hesitant to mess with my current set up until i get familiarized with it first.  is this do-able?  :) 
thanks!

Here is a good way to burn the disk. From the terminal, do:
hdiutil burn name-of-file.iso

You can boot from the live cd.  Just hold down the c key when you boot.

The mac boot manager knows about Linux.  Hold down the option key ( or alt key on a pc keyboard ).  You will get up a list of icons.  Select the Linux one you want.  The mac boot manager will find one operating system per partition.

Here what I would try.  
Mac OS PPC can boot from a firewire drive.  Install Ubuntu on a partition on your firewire harddrive.  Bring up the mac boot manager. Select linux. Press return.

Robert

---

### Post by 3rdalbum on 2007-04-22
Ignore scrooge's post - he/she has obviously not used Linux on PowerPC before. Rccharles has posted the right information for you.

---

### Post by scrooge_74 on 2007-04-22
> **3rdalbum said:**
> Ignore scrooge's post - he/she has obviously not used Linux on PowerPC before. Rccharles has posted the right information for you.

I stand corrected! :lolflag:

---

