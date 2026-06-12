---
title: "&quot;Starting Os ...&quot; then hang! Booting XP from Grub"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by tom.clements on 2007-04-26
OK, posting has kind of been my last resort because I know there are quite a few threads and sites on how to configure grub.. but for the life of me I can't work out why I can't get XP to boot. I have a three HDD setup, all are SATA and I have reduced the complexity of the drive setup and partiioning down to what I think is the simplest I could make it (previously I had two drives on a Fake RAID - which I got rid of because I don't think I gained much, with Ubuntu and XP on the same drive).

So, here is the output from an fdisk -L

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS               (Windows XP)

/dev/sdb1               1        5005    40202631    7  HPFS/NTFS                  (A audio / video scratch drive)

/dev/sdc1   *           1        4795    38515806   83  Linux
/dev/sdc2            4796        5005     1686825    5  Extended
/dev/sdc5            4796        5005     1686793+  82  Linux swap / Solaris

Grub is installed in the MBR of the Windows drive (sda) and is quite happy to load. Ubuntu boots just fine, but XP always hangs at "Starting OS ..." whenever I chose it. Relevant portion of my menu.lst is below:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7ee4537e-e5ec-4d3f-969b-790a348f8b2d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7ee4537e-e5ec-4d3f-969b-790a348f8b2d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

My understanding is that sda1 translates to (hd0,0) in grub so this looks ok, and as it is the first drive I don't need to use mapping. The bios is configured to boot this drive first.. in the other more complex setups I had previously, this was always the same result when I had configured menu.lst as I thought it should be i..e could boot Ubuntu but not XP with the same error.

I can consistently recover my XP by using fixmbr / fixboot, and then reinstalling grub brings me back to where I am. It is baffling, this is my third install of Ubuntu and the first to encounter this problem, although it is also the first where I have solely SATA drives. I should also note that I have CD-Writer and a DVD writer both on master IDE channels 1 and 2, the SATA drives the bios lists from 3 onwards.

Anyone got any ideas? I'm loathed to reinstall XP, but could if necessary, but I don't feel like I should need to!

Many thanks in advance,

Tom.

---

### Post by dstew on 2007-04-26
It looks like it is set up correctly. One thought I have is to try **rootnoverify** instead of **root** in your Windows grub list item.

---

### Post by tom.clements on 2007-04-26
thanks for the reply. Sorry, I should have added to my post - unfortunately I have tried that with no difference..

---

### Post by dstew on 2007-04-26
It is acting like the Windows chainloader is not working. Grub does not give an error, so at least grub thinks it has done its job. Is it possible that the Windows booter is not present in the first sector of its partition? If so, you might get this behavior.

The command **fixboot** is supposed to restore the booter. If you issue this from the Windows recovery console, without doing **fixmbr**, that might help.

---

### Post by tom.clements on 2007-04-27
thanks - tried that this morning.. and still no difference! Its very frustrating!

---

### Post by louieb on 2007-04-27
Just for grins. Do you have a Super GRUB Disk? See if you can get XP to boot with it. I don't have multiple SATA drives or I would play around with it. I know I'm not much help but since you have tried rootnoverify all I can say is I don't see anything wrong either. Very weird!

---

### Post by tom.clements on 2007-04-28
yep - I've tried super grub disk too and it won't boot xp - I just get a blank screen.. which I guess is not dissimilar behaviour to grub appearing to hang at the "Starting os ... " screen... 

wierd, frustrating? Certainly is!

---

### Post by Ocelaris on 2007-04-29
bump for the same problem, I had 6.10 working fine, but reinstalled 7.10 and playing with Super Grub Disk to get it working again...

*edit*

I gave up on 7.04, reinstalled 6.10 and everything is hunk dorey again... it has to do with everything being named SD instead of HD I think. Because I have SCSI, SATA, and PATA, and I think that confused it... will try again when I'm feeling more brave.

---

### Post by tom.clements on 2007-04-29
thats very useful to know.. I think I might go back to 6.10 just to get my system back on track.. hopefully it will work as well. Its good to know I'm not the only person having these knds of issues!

---

