---
title: "Duel Boot XP and Fiesty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-04-24
I have xp on one harddrive and fiesty on another can I make the one with fiesty a slave and then duel boot.  This sounds too simple to me so what do I need to do inorder to get this done, do I need to reinstall fiesty.  Please help me with this, thanks

---

### Post by freebird54 on 2007-04-24
Yes, you can.  The only problem is that if XP controls the boot, it won't know how to boot Linux.  The other way around is easier for that reason.  But - still doable a couple of different ways.

1.  Install grub (a bootloader from Linux) onto the MBR of your Windows drive.  Provided it knows that the rest of what it needs are on the Linux, drive, it prvides a choice, and you choose what comes up.

2. Switch the boot order in your BIOS between drives, depending which one you want to see.

---

