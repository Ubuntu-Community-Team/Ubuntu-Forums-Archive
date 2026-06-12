---
title: "Boot error (absolute Beginner)"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Unda on 2007-05-01
Hello all, 

Just wanted to say, then i'm completely new to both linux and ubuntu, I have tried Suse before but more than booting it than 5 times I haven't got any knowledge whatsoever about linux.

I'm currently using a dualboot Ubuntu/Win XP pc, I was able to install ubuntu, but further than the bootscreen I haven't come...

I have the following error:

> * Loading kernel modules...
* Loading Manual Drivers
* Activating swap
sck 1.40-WIP (14 nov 2006)
/dev/sda6: Superblock last mount time is in the future. FIXED
/dev/sda6: Superblock last write time is in the future. FIXED
/dev/sda6 has gone 49710 days without being checked, check forced
   50.5200001 bcw43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
firmware_helper[4119]: main error loading '/lib/firmware/bcm43xx_microcode5.fw'
for devicde '/class/firmware/0000:03:00.0' with driver '(unknown)'
/dev/sda6: |=================================     \ 52,5%

and then the boot hangs, and nothing happens.

anyone knows what to do?
I have a root / (8gig)
and a swap (2,5 gig)

thanks in forward,
Unda

---

### Post by taurus on 2007-05-01
Can you boot your machine into recovery mode from GRUB menu?  If you can, can you post the output of this command here?

```
fdisk -l
```
Otherwise, boot with the LiveCD and post this output here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Unda on 2007-05-01
thanks for the quick reply,

and no, I cannot boot in recovery mode, same error occures

when going in the live cd, I get this and running the command, this is the result:

> disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot    Start               End               Blocks                   id                      System
/dev/sda1   *          1                  3187            25599546             7                       HPFS/NTFS
/dev/sda2            3188               12161          72082655             f                       W95 Ext'd (LBA)
/dev/sda5            3188               10887          618443623           7                      HPFS/NTFS
/dev/sda6            10888             11860          7815591               83                    Linux
/dev/sda7            11861             12161          2417751               82                    Linux swap / Solaris

---

### Post by taurus on 2007-05-01
From the LiveCD, run

```
sudo fsck /dev/sda6
```

---

### Post by Unda on 2007-05-01
ok, I have done that... 

Now when I try to boot from my harddisk, the only thing I get is a black screen, and nothing happens. I somewhat had the same error during the installation and was able to fix that by putting acpi=off in the bootline, how do I fix it when booting from harddisk?

---

### Post by Unda on 2007-05-01
ok, I have managed to bypass the black screen, editted the bootline and I have put acpi=off before the root= ....
but the troubles aren't over yet, now I'm able to fill in my credentials, after filling in my credentials, I see the orangy/pink screen, with my mousecursor on it, I can move the mouse, but that's it, no other thingies happen. only the pink screen and the mouse, no toolbars, no icons...

---

### Post by Unda on 2007-05-01
bump *sorry*

---

### Post by mattnedgus on 2007-05-08
The same thing happens to me.

I have ubuntu fully installed and working on 1 laptop in dual boot configuration.

I have tried to do the same on an older laptop, to no avail.

The computer has various errors.  The first is the fsck error recorded here: [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/43239](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/43239)

The second is as Unda mentioned.  Once you do get to the login screen, you can get passed but it wont boot the user interface.  Only the mouse cursor is visible.

I have tried installing various ways including using ext2 and ext3 filesystems and loading a different locality (the Azores - to force a GMT+0 timestamp).

The liveCD does boot however...  and I have just noticed that the date is displayed "May 8" whereas on my system it is "8 May".  Could this be significant?  The other laptops date is rearranged in the BIOS to the American standard (MMDDYYYY) rather than the UK standard (DDMMYYYY).

I would be grateful if anyone can point me in the right direction, but I am about to try reinstalling Ubuntu 7.04 again but in an American locality...

---

### Post by mattnedgus on 2007-05-08
I'm confident that this is the problem I am witnessing:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/89069](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/89069)

I believe my personal problem could be due to the motherboard setup conflicting with the locality and somewhere along the way, the dates are getting screwed up.  As I say, the liveCD works fine - possibly because it runs more tests on the computer to determine the actual time zone.  Wheras when the zone is set by the user upon installation, a conflict is created.

I haven't managed to get it working yet... but the computer is re-installing for a US timezone as we speak - fingers crossed!

---

