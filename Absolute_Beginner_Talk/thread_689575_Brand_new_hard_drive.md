---
title: "Brand new hard drive"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Miller12 on 2008-02-06
I got a Dell Inspiron 5150 laptop from my brother who was told the HDD was toast. I bought a new HDD and put it in. Ran the Ubuntu LiveCD and was trying to install it but when I got to the partitions step (#4) I wasn't able to do anything - the Device, etc table was blank.

The HDD was bought at a computer store so it has not been formatted. Do I need to run gparted LiveCD and set up 3 partitions for OS, swap and /home? This will be a Ubuntu only laptop.

Thank you.

---

### Post by jken146 on 2008-02-06
You don't need to format it prior to running the installer.  Type ```
sudo fdisk -l
``` to see if the hard disk has been detected.  You can post what it says.

---

### Post by lswest on 2008-02-06
what might also be the problem is that the cable to the motherboard is broken, which would explain why both HDDs weren't recognized.  Not sure, may just be a loose connection at the moment too.  In any case, try the software side of things first, hardware is always a bit trickier to sort out.

---

### Post by wolfen69 on 2008-02-06
you can always choose "use entire disk" and it will format and create partitions automatically.

---

### Post by Miller12 on 2008-02-06
Looks like it must be a HDD to motherboard issue:

fdisk -l (I had to try fdisk -l /dev/hda): unable to find
BIOS doesn't see it
I tried a Windows disk and it didn't see it either

I looked at the user manual and there are no instructions for removing the bottom cover. Can I just unscrew it and pull the cover off or are there going to be attachments made to it?

If I do get in there is the cable going to have plugs on both ends ie: 1 to the HDD and 1 to the motherboard) or is something going to be soldered (in which case I better take it to the shop)?

Thank you.

@wolfen69 - there was no option to use the entire disk. Just the device table, partitions, path, etc which was blank. It says I must create a "/" and swap partition but there is nowhere for me to do anything.

---

### Post by Miller12 on 2008-02-06
I found the disassembly manual on the Dell site but it will have to wait until the weekend.

---

