---
title: "failed install, need to remove ubuntu"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ensignmessink on 2007-03-18
Unfortunately, my attempt to install Ubuntu on my laptop has failed miserably. For the moment I have decided not do do any more attempts. Perhaps with the next version of Ubuntu I'll try again.
Right now, I need to remove Linux from my computer altogether because windows has gotten some quirks since Linux failed to install and I do'nt want to get any more. At the moment it is only limited to refusing to play games, my computer won't load them. Can anyone tell me how remove linux without having to install windows again?

---

### Post by oilchangeguy on 2007-03-18
what version of windows are you running?

---

### Post by ensignmessink on 2007-03-18
XP Home, service pack 2

---

### Post by ensignmessink on 2007-03-18
I wouldn't know if it matters, but my laptop is an Acer Aspire 5100, AMD 64bit dual core processor, 1GB DDR2, 128mb videocard(Radeon Xpress 1100). I have used partition magic to create swap and ext3 partitions for linux and my current  bootloader is Grub.

---

### Post by oilchangeguy on 2007-03-18
ok, not in front of an xp box right now, so this is from memory. go to start, control panel, admin serv, computer mgt, disk mgt, and you should be able to see the partitions on the hard drive. and delete the linux partition. but if you're booting from grub you'll need to be able to fix windows master boot record (mbr). and the only way to do that is if you have an actual windows disc, not the factory restore disc. however since you're having problems with windows, starting fresh might not be such a bad idea. just back up any data on windows.

---

### Post by oilchangeguy on 2007-03-18
just saw your post about partition magic. why not let ubuntu pick how it wants to set up it's partitions? from the live cd just select the option to allow ubuntu to use the largest unused partition. and it'll do a fine job of doing the rest. no need to manually partition.

---

### Post by ensignmessink on 2007-03-18
I'm only having problems with my games, for the rest windows is functioning perfectly. But thanks anyway. If I have the original disc, it is not necessary to install windows itself? I hope I got that right.

---

### Post by oilchangeguy on 2007-03-18
this is only if you have a stand alone windows disc. not a factory restore disc. boot from the windows disc and select r when prompted to enter the recovery console. from there at the command prompt type fixmbr and press enter.

---

