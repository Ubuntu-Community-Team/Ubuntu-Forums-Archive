---
title: "Linux back to windows, if needed"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by klemens on 2005-11-11
I had a mandrake installation on an other machine, when i tried to reinstall windows it failed because of a boot sector error (sry don't remember with one).

If i install ubuntu now, can i simply reinstall windows without problems, or what do i have to do?
This is the last thing i would like to know before installing ubuntu and to try it out, i'm writing this on a life cd.

Thanks for the help!

---

### Post by kevcart3 on 2005-11-11
What I would suggest:

Create you two partitions on your hard drives, install windows on one FIRST.

Install Ubuntu on the second partition and let it set up GRUB for you so that you will be able to boot into Windows/Linux more easily.

That way you got both operating systems and you can go back and forth, and If you feel you don't need windows later, just uninstall it.

---

### Post by manicka on 2005-11-11
It would be easier to reinstall windows onto the machine first, then ubuntu

---

### Post by klemens on 2005-11-11
I wasn't thinking about a dual boot, but it's a good idea, i'll give it a try.
Thanks, be back later on ubuntu lol.

---

### Post by codejunkie on 2005-11-11
[quote=klemens]I had a mandrake installation on an other machine, when i tried to reinstall windows it failed because of a boot sector error (sry don't remember with one).

If i install ubuntu now, can i simply reinstall windows without problems, or what do i have to do?
This is the last thing i would like to know before installing ubuntu and to try it out, i'm writing this on a life cd.

Thanks for the help![/quote] yes you can restore the boot sector, if you wan't to go back to windows. you'll need the windows xp cd if that's what version of windows your using, put the cd in and boot from it like your going to do a clean install, but you'll see an option for recovery console use that instead. when you get to the command prompt type fixmbr hit enter when it's done type exit this will reboot the computer let it boot off the hdd instead of the cd and you should see the default windows boot loader instead of grub. that is if you have the windows xp cd and not a restore cd set that some pc manufactures provide.if your using a different version of windows like me,95,98 you'll need a boot floppy, boot from it when you get to the command prompt type fdisk /mbr this will restore the mbr on older windows systems but just incase it's always best to backup your important data first becuse sometimes things can go wrong.

---

### Post by patrick295767 on 2005-11-11
[QUOTE=kevcart3]What I would suggest:

Create you two partitions on your hard drives, install windows on one FIRST.

Install Ubuntu on the second partition and let it set up GRUB for you so that you will be able to boot into Windows/Linux more easily.

That way you got both operating systems and you can go back and forth, and If you feel you don't need windows later, just uninstall it.[/QUOTE]
  
I observed that to resize ext3 linux partition : it can only be done to the right direction of the harddisk !!
I am right ?
  
I then have on left side of my hdd, the swap, then the linux, then my windows stuffs
windows partitions can be resize both right and left !
  
I guess i am right no ?

---

