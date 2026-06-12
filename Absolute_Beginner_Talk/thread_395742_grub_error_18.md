---
title: "grub error 18"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by c174 on 2007-03-28
I'm running Ubuntu Edgy Eft, and the system has all updates. Here's my problem:

1) I turned on my computer, saw it reaching the log-in prompt.
2) Went out shopping bread and stuff
3) Back home, trying to log on to Ubuntu the keyboard was frozen
4) Reboot using ctrl+alt+del+backspace FAILED with Grub Error 18

What is wrong? I posted this using the Ubuntu installation disk.

I have two 80 GB Sata disks running as IDE. CDROM is secondary master. This setup has worked for a long time (3 years since I got the machine), only sometimes during boot up the hard-disks are not detected. In that case I just press "reset" one (or more times) and then it works. Maybe this indicates an error? A hardware error??

---

### Post by Repabil on 2007-03-28
Would you like to post the config file of the grub you use that gives the error?

---

### Post by c174 on 2007-03-28
Yes, I would like to, but dont know how.... I'm currently running Ubuntu from the installation disk. Can I acces files from my harddisk?

---

### Post by Repabil on 2007-03-28
If you're hard drive is has been mounted I think you can find it on your desktop. Open it and browse to */boot/grub/menu.lst*. If it isn't on your desktop you may have to mount it manually. Don't mix config file on your hard drive up with the one on the live-CD.

---

### Post by c174 on 2007-03-28
Okay, sorry for being slow.... How do I mount a harddisk? (not found on the desktop or in "places")

I tried: mount hda0, but received: mount: can't find hda0 in /etc/fstab or /etc/mtab

I think these locations refer to the Ubuntu-cdrom...

---

### Post by Repabil on 2007-03-29
> **c174 said:**
> Okay, sorry for being slow.... How do I mount a harddisk? (not found on the desktop or in "places")

I tried: mount hda0, but received: mount: can't find hda0 in /etc/fstab or /etc/mtab

I think these locations refer to the Ubuntu-cdrom...
No problem. You can try do it with System -> Admin -> Disks and choosing the disk in question, then the said partition and press enable to be able to browse it.

---

### Post by mcduck on 2007-03-29
Grub error 18 tells that the partition is bigger than what your BIOS supports. As you told you have problems with BIOS not always detecting your disks you should first check that the cables are fine and properly connected, and then check that you have correct settings for the disks in BIOS. If either one is wrong BIOS might thing have wrong settings for your disk sizes, thinking that they are much bigger than it supports.

---

### Post by c174 on 2007-03-30
Thank you guys!

I checked BOIS and found that I had a "combined S-ATA and P-ATA". I don't know if that is really wrong, but I changed it anyhow to just "S-ATA".

I read something on the net about the boot-partion should be within the first 8 GB on the disk, so that BIOS can seach deep enough, so I have repartioned my system -- unfortunately I missed up everything. So I lost all data and have now a fresh system... :-|

---

