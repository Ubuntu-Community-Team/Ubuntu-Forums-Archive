---
title: "problem with drive"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by cloned on 2006-10-17
alright so i went to delete the windows partion before installing linux on my old laptop and now i can't access the C drive outside of fdisk and the CD drive is not working?

i was thinking that if i can install win 98 then i can be able to install ubuntu, also i have many bootdisks that work but i cna't seem to be able to use format on the C drive. if i do ever get windows back on it it will only have 2 GB of the 18 GB HDD and will only have win 98 on it as a back up if i need to reinstall linux

can someone help me on this?

---

### Post by TheWizzard on 2006-10-17
can you explain what you did with more detail?

you don't need to install win98 to install ubuntu.
is your CD the first to boot from in your bios?

---

### Post by caravel on 2006-10-17
You need to enter your CMOS setup utility and enter BIOS Features -> Boot Sequence, or something similar and set the CDROM drive as the first drive in the sequence.  Then reboot with the installation CD in drive.  The LiveCD will then boot and you can install Ubuntu from the install icon on the desktop.  You don't need any kind of Windows or other OS to install from.

There is a possibility that the BIOS on your 'old laptop' doesn't support booting from ATAPI devices, this depends on how old the old laptop is, if this is the case then there is usually a way to boot from a floppy *loading the kernel module for the CDROM in the process.**

*not sure about that though as I'm a Linux/Ubuntu newbie myself.

---

### Post by cloned on 2006-10-17
actualy yes i did set it to boot the CD drive first but it won't let me access it and when i don't have a floppy drive in it the screen says "no operating system installed" so i am trying to at least install DOS because i have any old external CD drive that works in DOS so i have a back up if my CD drive turns out to be dead.

the CD drive does tend to overheat a lot at least when anything was being run under windows

the laptop is about 5 years old

sorry it took awhile for me to reply, it was very late for me and i needed sleep

also i can not seem to be able to even use format off the floppy disk

DIT: for some reason it is starting to do what i want this morning, yet last night is kept calling the C drive a network drive

---

