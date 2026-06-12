---
title: "Missing operating system"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ElfKing on 2007-05-25
I got throught he installing process to the point that it said "about to install to HD0" and aborted.  Now my system won't let me boot up windows.  Says it's missing an operating system.  Also will not let me boot from cd (windows) but will let me boot to Ubuntu from the CD.  Anyone have a ny thoughts on what happened and how to solve it?  Thanks to anyone who does!!!

---

### Post by init1 on 2007-05-25
The "install to HD0" is vital. Your computer cannot boot with a damaged or incomplete bootloader, the program that lets you choose whether to boot linux or windows. The easiest way is just install Ubuntu again. Be sure that you install it correctly, or it will write over windows.

---

### Post by ElfKing on 2007-05-25
so if I  let the install to HD0 it won't overwrite my windows partition?

---

### Post by init1 on 2007-05-25
HD0 is grub's (what allows to boot ether windows or linux at startup) way of identifying your hard drive. If you had two hard drives, the second one would probably appear as HD1. It will install to the MBR of your hard drive and will not write over your windows partition. I Hope this helped!

---

