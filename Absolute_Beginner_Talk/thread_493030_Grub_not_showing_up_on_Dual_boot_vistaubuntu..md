---
title: "Grub not showing up on Dual boot vista/ubuntu."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Hyrup on 2007-07-05
I have 1 hard drive with Vista and made a separate partition on it for Ubuntu.  Installation went fine, but when it came to choosing a Grub location, I choose hd0,4 (which is my sda5 location...where ubuntu is).  When I run a terminal in the livecd, Grub tells me its install in hd0,4...so it is there.  However when I boot my comp, I don't see the menu and I just load right into vista.

Any help would be great!

---

### Post by edwardLS on 2007-07-05
I believe I understand your situation, and if I do - here's my take.

When you installed grub in (hd0,4) you did not put it in the Master Boot Record.  To put grub in the MBR you would select (hd0).  When your computer starts, the BIOS only know how to first go to the MBR of the first HDD.  Thus, you will be booting Vista.

---

### Post by confused57 on 2007-07-05
> **Hyrup said:**
> I have 1 hard drive with Vista and made a separate partition on it for Ubuntu.  Installation went fine, but when it came to choosing a Grub location, I choose hd0,4 (which is my sda5 location...where ubuntu is).  When I run a terminal in the livecd, Grub tells me its install in hd0,4...so it is there.  However when I boot my comp, I don't see the menu and I just load right into vista.

Any help would be great!
Just use the Vista bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Hyrup on 2007-07-07
Got it working, thanks:popcorn:

---

