---
title: "grub problem"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by andyfonforum on 2006-12-02
hi
Grub, boot loader has loaded not quite correctly.
Have just loaded Ubuntu from a disk that came with book on linux, do not understand the file system or anything yet and am thankful I can log on to this site.  (Beleive my version is Dapper Drake)
I have bootable Windows 98 SE on two other partitions on the drive plus logical partition with windows data, but Grub has not recognised it so that I can boot back into it.  In Windows I used Partion Magic, BootMagic to select and boot into my two windows partitions, (both were the same - one is just a back up).  All my windows partitions are shown on the Ubuntu desktop and I can see all the files, no files/partitions have been lost or currupted.   Grub seems to have installed itself (it never asked permission!) and has consequently wiped BootMagic.
Can any one tell me how to configure Grub to boot my Windows partitions in a step by step guide because I do not know how to find my way around this file system,:confused:  let alone tricky stuff like boot tables or script? Regards Andy.

---

### Post by indytim on 2006-12-02
Grub will automatically install when you do your initial Ubuntu (or Kubuntu) installation.  When you boot up cold, do you see the options for your Windows environment?  The Windows options are politely put at the bottom of the boot options.  You have to look quick as I think GRUB defaults to a 3 or 5 second dwell time before reverting to the default (Ubuntu).

Post back your results from the above and someone should be able to help you get your system happy again.

IndyTim

---

### Post by infoseeker on 2006-12-02
The moment the grub screen appears, tap the down arrow on your keyboard.  This disables the timeout, and the menus items will be visible for as long as you like.

welcome to Linux.

---

### Post by andyfonforum on 2006-12-02
> **indytim said:**
> Grub will automatically install when you do your initial Ubuntu (or Kubuntu) installation.  When you boot up cold, do you see the options for your Windows environment?  The Windows options are politely put at the bottom of the boot options.  You have to look quick as I think GRUB defaults to a 3 or 5 second dwell time before reverting to the default (Ubuntu).

Post back your results from the above and someone should be able to help you get your system happy again.

IndyTim


I think I did not expain myself very well for which I apologise - have had a nose around the forum and the files on my computer I begin to understand the question I should ask so I have put a new thread in the forum (refers to this one) but asks the question better - thanks for your patience - andy

---

### Post by andyfonforum on 2006-12-02
> **infoseeker said:**
> The moment the grub screen appears, tap the down arrow on your keyboard.  This disables the timeout, and the menus items will be visible for as long as you like.

welcome to Linux.




I think I did not expain myself very well for which I apologise - have had a nose around the forum and the files on my computer I begin to understand the question I should ask so I have put a new thread in the forum (refers to this one) but asks the question better - thanks for your patience - andy

---

