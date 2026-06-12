---
title: "Removing Ubuntu, or GRUB boot up"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by sparks_clark on 2007-07-05
I am having extream crashing issues with the dual boot between XP and Ubuntu.  I have a major project that I need windows software for but after I run windows I my computer will continuously reboot after GRUB stage 1.5 appears on the start up.  Effectively locking me out of the computer.  Every time this happens I have to reinstall ubuntu just so i can get back to the dual boot menu so I can load windows.   As great as this community is and how much I like the OS I can not drop windows at this point in my life.  So sadly I must drop ubuntu (unless someone has a better idea how i can have my cake and eat it too).  How do I go about removing the boot up commands that have been placed into my initial boot sequence (on my XP/main hard drive)?

Thanks, Sparks

---

### Post by kosmic on 2007-07-05
Just boot with your Windows installation CD and do a rescue, the key to press I think it is F3.

then use fdisk to write a new boot.

in the terminal that windows installer gives you (DOS)

type

fdisk /MBR

after that reboot and voila...no more grub :(

---

### Post by Nekiruhs on 2007-07-05
Pop in a XP CD, get to DOS and type FIXMBR. That will restore your normal XP boot.

---

