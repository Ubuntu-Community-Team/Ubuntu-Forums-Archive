---
title: "Installation fails. Computer hangsup."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by 5tudent on 2006-02-23
Hi.

I am a newbie to Unix/Linux and am trying to install Ubuntu 5.10 on an old Dell Poweredge machine with dual hard disks and 256MB RAM.

This is what I want to do:
Install Ubuntu on hard disk, overwriting, any and all contents, of the said hard disks. I would prefer to install Ubunto on HardDisk #2, as Disk #1 might have bad sectors.

Note: Both hard disks do NOT contain any OS. Contents of both hard disks can be erased. BIOS confirms the presence of both hard disks and recognises correct capacity of both hard disks.

This is what I did:
a) Used the live CD and booted the machine. Everything works and I am able to even surf the web.

b) Rebooted the machine using the "Installation CD". Chose the option "Erase everything on hd2". Chose "Auto partition" of hard disk.

c) The installer displays a message, to the effect, "Remove the CD, reboot the machine, to complete the install".

d) I removed the CD and rebooted the machine.

I get the word "GRUB" followed by a blinking cursor.
Nothing happens (viz. No screen refresh, No activity) thereafter.

On typing any key on the keyboard, I get a beep sound.

Please advise. Please give detailed steps.

Thanking you in advance.

---

### Post by Kurt` on 2006-02-23
On one of my old machines (500mhz, 64meg ram), the "Loading Grub..." prompt would sit there for almost 2 minutes before the menu popped up... long shot, but try waiting it out (within reason).

Otherwise, there may have been a problem writing grub to your MBR, which might be a little more difficult to debug. :)

---

