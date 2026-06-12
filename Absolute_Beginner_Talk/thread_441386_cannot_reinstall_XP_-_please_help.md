---
title: "cannot reinstall XP - please help"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-12
I'm in an odd predicament.  My Thinkpad T43 comes with a partition that lets me "reset the hard drive to factory settings" and this was my sequence of events:

1. Formatted hard drive and reinstalled XP from the Thinkpad partition - was successful
2. Installed Ubuntu (Feisty) - was successful

Things were beautiful.  Then I figured out that I selected 25% of my hard disk space to XP and 75% to Ubuntu, which was the opposite of what I wanted.  So I thought, ok, let me just start over.

3, Reformatted hard drive and reinstalled XP from the Thinkpad partition

Would not let me boot - gave me a GRUB error.  So I thought, alright, I'll just install Ubuntu again to get GRUB

4. Reinstalled Ubuntu

Now when I restart the computer, I get the GRUB screen that lets me select which OS to boot.  When I select Ubuntu, things are fine.  But when I select XP, I get this -

"Invalid system disk
Replace the disk, and press any key"

When I press any key, I go back to the GRUB menu options.  Basically I'm unable to boot into XP  - please help!

---

### Post by starcraft.man on 2007-05-12
Your error at section 3 doesn't make any sense... I used to have an OEM hidden partition to reinstall and it restored the MBR just in case I had caused any problems to it (I actually did damage it twice, call me dangerous :p). That means one of two things to me:

1) Your OEM was cheap and didn't expect you to modify the MBR ever and only made it so that it would restore files to the original partition (I find it unlikely).

2) You formatted/overwrote your hidden partition from your OEM.

Can you do a simple check for me, boot into Ubuntu and open the terminal Applications > Accessories > Terminal, then type this :

```
sudo fdisk -l
```

That should do it, then I can tell you more :)

---

### Post by sthapit on 2007-05-12
here it is (p.s. I'm pretty sure I didn't format the hidden partition - I was pretty mindful about the options when I was installing Ubuntu to avoid losing XP).  thanks for any help.

sthapit@T43:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6606    53062663+   c  W95 FAT32 (LBA)
/dev/sda2            9216        9729     4127760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            6607        9101    20041087+  83  Linux
/dev/sda4            9102        9215      915705    5  Extended
/dev/sda5            9102        9215      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by starcraft.man on 2007-05-12
> **sthapit said:**
> here it is (p.s. I'm pretty sure I didn't format the hidden partition - I was pretty mindful about the options when I was installing Ubuntu to avoid losing XP).  thanks for any help.

sthapit@T43:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6606    53062663+   c  W95 FAT32 (LBA)
/dev/sda2            9216        9729     4127760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            6607        9101    20041087+  83  Linux
/dev/sda4            9102        9215      915705    5  Extended
/dev/sda5            9102        9215      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order

This is why I hate stupid OEM hidden partitions, they should just give people CDs. (course then you wouldn't have to put up with their installed crap every time you reinstalled). I am wondering why you get the warning "Partition 2 does not end on cylinder boundary", but I doubt thats the issue.

I'm gonna guess that maybe something simply went wrong with the reinstall, boot back into your recovery partition and make sure you select the option which completely sets you back to factory. If this fails again, there is something seriously wrong with your OEM partition, that is not overwriting the MBR, and I don't believe there is a way to use the fix mbr command from the partition.

So, after reinstalling again, if it fails a second time. My suggestion is to use [GAG]("http://gag.sourceforge.net/") just pop it in and it will overwrite the MBR and detect any partitions with OS's on it. If you find that you cannot boot into XP at all from GAG too, then there is a serious issue/corruption with your OEM partition.

I would suggest you take back your rights and go get a copy of a Windows installer disk from bit torrent, get the OEM version of whichever windows you have (home/pro/MCE) and use your key, it will work.

---

