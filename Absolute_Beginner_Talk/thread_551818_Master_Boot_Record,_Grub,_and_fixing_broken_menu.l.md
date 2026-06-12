---
title: "Master Boot Record, Grub, and fixing broken menu.lst"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-15
I see a Tutorial/How-To 

HOWTO: Restore GRUB (if your MBR is messed up ([http://ubuntuforums.org/showthread.php?t=24113&highlight=master+boot+record](http://ubuntuforums.org/showthread.php?t=24113&highlight=master+boot+record))

[B]Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer[/B]

[COLOR="DarkOrange"]
the first post is from April of 2005. Can someone tell me if those instructions are still currently valid? Has Feisty's installation changed in some way since 2 1/2 years ago, so that if I run the installer, I will not harm my disk?[/COLOR]

---

### Post by alienexplorers on 2007-09-15
You could also run the live-cd and just restore grub from there.

---

### Post by Mark_in_Hollywood on 2007-09-17
> **alienexplorers said:**
> You could also run the live-cd and just restore grub from there.

Does that mean that ONLY grub would be "re-installed" or does it mean that all the software downloaded, configuration files and /home would be changed, overwritten, modified or made inaccessable?

---

### Post by Shazaam on 2007-09-17
All grub does is control the initial boot process. Another alternative to the Ubuntu LiveCD is to download and burn a SuperGrubDisk but you don't really learn the basics about grub.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Mark_in_Hollywood on 2007-09-17
Please, pardon me, but that isn't a response to my question. 

Technically,

In order to be able to get work done, I've swapped two hard drives. the problem disk was Primary Master and it was been set as Primary Slave.

Can I work on it from the LiveCD to restore grub from the slave position? How do I find the correct (hdx,x) numbers. How do I confirm that those are the correct number (i.e., switching drives on cable?, some Linux command like: uname -r?

currently:

Disk /dev/sda: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1181     9486351   83  Linux
/dev/sda2            1182        1240      473917+   5  Extended
/dev/sda5            1182        1240      473886   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4485    36025731   83  Linux
/dev/sdb2            4773        4865      747022+   5  Extended
/dev/sdb5            4773        4865      746991   82  Linux swap / Solaris


Please note that the disks are in the reverse cable positions from what I usually have them in.

---

