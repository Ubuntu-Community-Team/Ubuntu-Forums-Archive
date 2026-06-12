---
title: "Windows won't boot from the dual-boot :( not good!"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-05-29
Alright, I went through the process of creating partitions using gparted on the systemrescuecd.
Afterwards, I resized the NTFS of Windows XP.
Then, I created a partition of ext3 for Kubuntu.
Next, I left free space.

Alright, so I've been able to use Kubuntu just fine for the past while.
However, I recently started Windows XP back up, and it's not going through.
I was at GRUB to do all of this...

So, after choosing Windows XP Media Center, i'm at this black screen that says...

Starting up ...
_

the underscore is blinking, and the screen hasn't done anything for a while.
I don't know what's wrong, but I don't really want to reformat anything...

What do I do to get into Windows XP?

---

### Post by BarfBag on 2007-05-29
If you don't get any error messages from Grub, it's probably a Windows problem.  I'm sorry, but your Windows partition might not have made it through resizing the partition.  Unfortunately, that happens sometimes.  Try getting out your Windows CD and doing a repair.  This should try and fix the problem without deleting any data.  It clears the MBR, so you might have to reinstall Ubuntu afterwards.

---

### Post by Genecks on 2007-05-29
That's odd, because I gave my computer a complete reformat before installing Kubuntu. Other than that, do you think letting Windows control the boot process would prevent this from now on?

---

### Post by gdoermann on 2007-05-29
> **Genecks said:**
> Alright, I went through the process of creating partitions using gparted on the systemrescuecd.
Afterwards, I resized the NTFS of Windows XP.
Then, I created a partition of ext3 for Kubuntu.
Next, I left free space.

Alright, so I've been able to use Kubuntu just fine for the past while.
However, I recently started Windows XP back up, and it's not going through.
I was at GRUB to do all of this...

So, after choosing Windows XP Media Center, i'm at this black screen that says...

Starting up ...
_

the underscore is blinking, and the screen hasn't done anything for a while.
I don't know what's wrong, but I don't really want to reformat anything...

What do I do to get into Windows XP?

Have you ever gotten XP to work?  I would also probe what GRUB is doing. (/boot/grub/menu.lst)  This is a good reference for GRUB:  [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

P.S.  It would also be helpful to know your system specs.

---

