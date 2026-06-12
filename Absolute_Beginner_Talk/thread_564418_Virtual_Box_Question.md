---
title: "Virtual Box Question"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-10-01
I have had some very strange experiences with Virtual Box. My computer: Intel Core2Duo, 2Gig Ram, Nvidia card.
I am running Sabayon on one drive and Feisty and Feisty Studio on the other. Virtual Box comes as part of the package with Sabayon. I recently installed XP as a guest system into Sabayon. (Twice actually, I had to remove it once.)
After each time Ubuntu stopped half way through booting up. The loader was stuffed.
I hardly have any knowledge of the command line at all, but I have Super Grub Disc. After reinstalling grub everything was ok again. I have had a similar problem with VMWare on my old computer. (2.8Celeron.) I installed Sabayon as guest into Ubuntu Edgy. After rebooting the computer tried to boot into the Guest OS  (Sabayon) and stopped half way into the boot process.
I am not very worried right now, but I am very curious.
Are there any issues with Virtual Box and VMWare? Or have I made a mistake somewhere?:confused:

---

### Post by n3tfury on 2007-10-01
i'm not sure how using any of the VM's has anything to do with the boot loader.  you're either mistaken or you installed something incorrectly.  hopefully someone else can help you further.

---

### Post by kellemes on 2007-10-01
Virtual machines will basically do nothing with the "real machine".
Obviously.. reinstalling OS's you have to review the bootloader, and often reinstall..
And as you already learned.. SuperGrubDisk works great! :popcorn:

---

### Post by bodhi.zazen on 2007-10-01
The only potential source of interaction I can see would be if you were trying to physically boot your physical partition with VMWare or VirtualBox.

---

### Post by Chamelion on 2007-10-02
Thanks all. Let's see if anything happens when I load the next virtual machine. :)

---

