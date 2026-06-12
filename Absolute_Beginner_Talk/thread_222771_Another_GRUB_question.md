---
title: "Another GRUB question"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Styxke on 2006-07-25
Hi all,

I know this has been discussed several times already but I can't seem to find a solution.
I have one SATA and 2 PATA drives.
Device map:
```

/dev/hda = hd0
/dev/hdb = hd1
/dev/sda = hd2

```
WinXP is on the SATA drive (hd2,0), I installed ubuntu on the second PATA drive (hd1,1) , first partition is data. When I install in text mode I can install GRUB on hd2 and when I reboot I effectively get the boot menu BUT I can't start any of the OSes, not linux (partition doesn't exist) and not WinXP. 
After fiddling with the GRUB command line (find /boot/grub/stage1) I found the the linux entry must point to (hd2,1) and not (hd1) as in the device.map) ??
WinXP I can never start, that one points to (hd0,0 also different than the device.map) but it always says "NTLDR is missing".
I also tried grub4dos (after a reinstall of WinXP)... that made it even worse (nothing booted, error 26: Disk read error during stage 2).

Is my bios playing tricks on GRUB here (the device.map not being correct) ?

I can't give you the fdisk -l output at this moment nor the menu.lst because I needed to format the drive to get everything working again and I don't have internet on my ubuntu (yet).

Can someone help me, I'm at a loss ...

---

### Post by moore.bryan on 2006-07-25
sorry this won't help you much, but i gave up on multi=disk boot about a year ago... i wasn't able to get it to work.

---

### Post by BoneKracker on 2006-07-25
The GRUB manual:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

You should be able to boot from any live CD, the installer CD, or any GRUB disk to get access to your files.  If you boot from the liveCD, mount the partition containing your /boot directory, open /boot/grub/menu.lst in an editor, copy and paste it into a message here.

In the meantime, you can also continue to investigate on your own:

As noted above, read up on GRUB.  That's likely to be useful knowledge in the future.

Verify the paths in /boot/grub/menu.lst.  Lines beginning with "groot" or "root" (for the grub root, which is whatever partition your /boot directory resides in, in grub-style syntax), and "kernel" or "initrd" (for the linux root, which is the path to your / directory, in linux-style syntax). Verify that you've got a Windows boot alternative there as well.

---

### Post by Styxke on 2006-07-26
> **BoneKracker said:**
> The GRUB manual:

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

You should be able to boot from any live CD, the installer CD, or any GRUB disk to get access to your files.  If you boot from the liveCD, mount the partition containing your /boot directory, open /boot/grub/menu.lst in an editor, copy and paste it into a message here.


There lies the problem, I don't have an ineternet connection in ubuntu (it's wireless usb). But I will try tomorrow and post it here. 
But every time I get ubuntu to work I need to reinstall windows and that is an annoying job.

> 
In the meantime, you can also continue to investigate on your own:

As noted above, read up on GRUB.  That's likely to be useful knowledge in the future.

Verify the paths in /boot/grub/menu.lst.  Lines beginning with "groot" or "root" (for the grub root, which is whatever partition your /boot directory resides in, in grub-style syntax), and "kernel" or "initrd" (for the linux root, which is the path to your / directory, in linux-style syntax). Verify that you've got a Windows boot alternative there as well.


I already read the grub manual (I only post here as a last resort). The paths for ubuntu I can correct. But for windows I can set the root to hd0,hd1 or hd2 it always says that ntloader is missing ... ubuntu isn't really the problem although it
should detect settings correct in the future. It's windows that is the problem (and because I'm a gamer, I can't get rid of it yet).

---

### Post by Styxke on 2006-07-27
Here is the menu.lst Ubuntu generates:
```

title		Ubuntu, kernel 2.6.15-23-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

And the device.map:
```

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda

```

Note that the generated menu.lst doesn't work, the root needs to be (hd2,1) for it to boot while Ubuntu is installed on (hd1,1) according to device.map (and it is in fact really installed there). WindowsXP I can't boot regardless of which root I set for it ...
Any help would be much appreciated!

Thanks in advance.

---

### Post by steve.horsley on 2006-07-27
I suspect that device.map is wrong. Try using Esc at the grub menu to get a grub prompt and then try these commands to see if they help:> geometry (hd0)
geometry (hd1)
geometry (hd2)

---

### Post by Styxke on 2006-07-28
It's strange, in Ubuntu Grub gives me this:

```

grub> geometry (hd0)
drive 0x80: C/H/S = 15505/240/63, The number of sectors = 234441648, /dev/hda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/hdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd2)
drive 0x82: C/H/S = 4500/255/63, The number of sectors = 72303840, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

```


And at boot time:

```

grub> geometry (hd0)
drive 0x82: C/H/S = 4500/255/63, The number of sectors = 72303840
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x80: C/H/S = 15505/240/63, The number of sectors = 234441648
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x81: C/H/S = 14593/255/63, The number of sectors = 234441648
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```

What now ?

---

### Post by klytu on 2006-07-28
> **Styxke said:**
> Hi all,

I know this has been discussed several times already but I can't seem to find a solution.
I have one SATA and 2 PATA drives.
Device map:
```

/dev/hda = hd0
/dev/hdb = hd1
/dev/sda = hd2

```
WinXP is on the SATA drive (hd2,0), I installed ubuntu on the second PATA drive (hd1,1) , first partition is data. When I install in text mode I can install GRUB on hd2 and when I reboot I effectively get the boot menu BUT I can't start any of the OSes, not linux (partition doesn't exist) and not WinXP. 
After fiddling with the GRUB command line (find /boot/grub/stage1) I found the the linux entry must point to (hd2,1) and not (hd1) as in the device.map) ??
WinXP I can never start, that one points to (hd0,0 also different than the device.map) but it always says "NTLDR is missing".
I also tried grub4dos (after a reinstall of WinXP)... that made it even worse (nothing booted, error 26: Disk read error during stage 2).

Is my bios playing tricks on GRUB here (the device.map not being correct) ?

I can't give you the fdisk -l output at this moment nor the menu.lst because I needed to format the drive to get everything working again and I don't have internet on my ubuntu (yet).

Can someone help me, I'm at a loss ...

This is all more of an observation than a solution, but maybe some of my comments below may help. You state that you can install GRUB on (hd2). If you actually did that, I think you wiped out the WinXP bootloader which was the beginning of your trouble. 
Have you got WinXP up and running again yet on the SATA drive? Once you do, be careful where you install GRUB. I think you want to install GRUB on /dev/hdb, (or wherever you plan to install Ubuntu). If you first install WinXP, then Ubuntu it is possible also to have WinXP's bootloader remain in charge and select booting into Ubuntu (or passing control to GRUB which could then load Ubuntu). That might be a better plan for your situation.

I think maybe the reason why (when you fiddled with the command line) it seemed that the Linux entry had to point to (hd2,1) is because when you tried to boot WinXP the two drives were "swapped" by GRUB, then the XP boot failed leaving things in a state (at the time) where hd2 is mapped to hd1 and vice-versa.

Looking at your last post, I don't know why so many of your partitions are now showing up with "filesystem type unknown". But now it looks like you have Ubuntu on hd2 and no WinXP. What are you using to set up your partitions?

---

### Post by Styxke on 2006-07-29
> 
Looking at your last post, I don't know why so many of your partitions are now showing up with "filesystem type unknown". But now it looks like you have Ubuntu on hd2 and no WinXP. What are you using to set up your partitions?


I used the partitioner that comes with the Ubuntu installer ...
Any idea what I must put in the boot.ini in XP to let it show a second entry while booting and point it to grub now installed on (hd2) ?

---

### Post by klytu on 2006-07-29
> **Styxke said:**
> I used the partitioner that comes with the Ubuntu installer ...
Any idea what I must put in the boot.ini in XP to let it show a second entry while booting and point it to grub now installed on (hd2) ?

This may be helpful: [http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

The end of the how-to shows how to use dd to copy the the necessary information to a file which could then be referenced in boot.ini

---

### Post by Styxke on 2006-07-31
> 
This may be helpful: [http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

The end of the how-to shows how to use dd to copy the the necessary information to a file which could then be referenced in boot.ini


This did the trick ... thanks for all the help.

---

