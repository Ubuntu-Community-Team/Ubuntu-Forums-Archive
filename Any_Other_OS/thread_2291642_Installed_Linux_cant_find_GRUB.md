---
title: "Installed Linux cant find GRUB"
date: 2015-08-21
forum: Any Other OS
---

### Post by Kevin h II on 2015-08-21
Hello all i apologize for making a noob mistake yet ive run ubuntu previously but i ran an os on my desktop called Evolve OS and installed it just earlier today. the issue being the install went smooth til the grub came up it said where to install the grub /dev/sdb is where i chose as ive got a dual boot with windows XP. The install finished then i restarted and it never showed grub just went to windows and windows tried check disk i stopped it before it started searching the harddrive.

Question: how do i get the linux partition to launch/start when there is no GRUB popping up allowing me to select OS's. do i just remove the linux partition and start over but select dev/sda this time instead?

---

### Post by PaulW2U on 2015-08-21
Thread moved to **Any Other OS** as you're not running an official Ubuntu flavour.

---

### Post by oldfred on 2015-08-21
You need to go into BIOS and change default boot to drive that is sdb.

Some very old BIOS only let you boot from sda, or if extremely old and IDE/PATA drives with jumpers, the jumpers on hard drive control which drive is bootable. Newer IDE drives had cable select which let BIOS control boot drive, but you have to use the 80 conductor cables.

---

### Post by Bashing-om on 2015-08-21
Kevin h IIKevin h II; Hello;

Did you reset in bios to boot from the hard drive that Evolve OS is installed to ?

Show us what you are working with:
from the liveDVD booted to "try ubuntu" mode - or whatever   Evolve OS  offers:
activate a terminal and post back the outputs of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```

So we know the partitioning scheme and where linux is installed to.

Re-installing grub
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Kevin h II on 2015-08-21
im currently on the live disk of evolve os but the sudo parted -1 didn't work it doesn't recognize parted, but the disc is on if any one can quickly reply to what i do for the partitions on the system.

FAIL: i typed -1 not -l and heres the output of the code.

live@solus ~ $ sudo fdisk -lu
Disk /dev/loop0: 615.8 MiB, 645726208 bytes, 1261184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 512 MiB, 536870912 bytes, 1048576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x20cd20cc

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *       63 625121279 625121217 298.1G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x58f380c7

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *           63 413845503 413845441 197.3G  7 HPFS/NTFS/exFAT
/dev/sdb2       413845504 623044607 209199104  99.8G 83 Linux
/dev/sdb3       623044608 625141759   2097152     1G 82 Linux swap / Solaris




Disk /dev/mapper/live-rw: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/live-base: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
live@solus ~ $ ^C

---

### Post by Bashing-om on 2015-08-21
Kevin h II; Well;

Sorta at a loss as I do not know how :
> 
Disk /dev/mapper/live-rw: 
bk
Disk /dev/mapper/live-base: 4 GiB

relates to the install.

We have the info required to know that 'linux' is installed to the 2nd hard drive (sdb) and occupies the 2nd (sdb2) partition.
Other than this I am not qualified to offer advise as I do not know if this is a LVM relationship, and IF/how LVM might apply to the install.

As to 'parted -l' that is a lower case 'L' - not a numerial 1.

That all said this might be more than just
[INDENT][INDENT][INDENT][INDENT]a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kevin h II on 2015-08-21
would removing the partitions and reinstalling work, it only took 10 minutes to install the os anyway and i havent done anything on that linux partition so thats not much of a worry for me.

---

### Post by Bashing-om on 2015-08-21
Kevin h II wellll ...
No:
> 
would removing the partitions and reinstalling work,

As the system is installed ( apparently anyway ), seems this is but a bios/booting/grub issue.

I have no heartburn to advise on how to (RE-)install grub for a 'normal' ubuntu install situation. However I do not know that the boot process of ubuntu and Evolve OS are similar .

If you decide that the process is similar ;
Boot the liveDVD of Evolve OS to terminal:
execute terminal commands:
```

sudo mount /dev/sdb2 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

Reboot and reset in grub to boot from that 2nd hard drive.
Once in the installed operating system, activate a terminal and now execute terminal command:
```

sudo update-grub

```
insuring that Windows is picked up and chainloaded onto the linux grub boot menu.
This procedure leaves the Windows boot code alone on the 1st hard drive, thus one can select which hard drive to boot from by selecting in bios which drive to boot .

[INDENT][INDENT][INDENT]maybe
[/INDENT][/INDENT][/INDENT]

---

### Post by Kevin h II on 2015-08-21
im unsure if these are viable options as my desktop is a dell xps 400 aka dimension 9150 4gbs ddr2 ram 2x 300 gb western digital drives, the bios is A07. as well the command heres the output

live@solus ~ $ sudo mount /dev/sdb2 /mnt
live@solus ~ $ sudo grub-install --boot-directory=/mnt /dev/sdb
/usr/sbin/grub-bios-setup: warning: this LDM has no Embedding Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.
live@solus ~ $

---

### Post by Bashing-om on 2015-08-21
Kevin h II; Uh Huh ;

That answers that . Not the same same as 'buntu's boot process.

Will take others to advise on what that situation is.

[INDENT][INDENT]one of those rare times
[INDENT][INDENT][INDENT]I do not want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kevin h II on 2015-08-21
now i wait, my elder brothers a unix and linux server manager but hes not home currently i could ask him for any advice but this may not be fixable other than reinstall evolve os but select sda

---

### Post by Kevin h II on 2015-08-21
im looking through the file manager with the live disc and realized that the raid didnt interfere with partitions that bizarre normally i have mass head ache due to raid on this desktop this shouldnt be to difficult to resolve the grub loader then :D

---

### Post by Bashing-om on 2015-08-21
Kevin h II; Hey.

Hardware raid or software raid ?
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Most levels of raid, the bootcode must be installed outside of the raid arrays .

[INDENT][INDENT]A horse of a different color
[/INDENT][/INDENT]

---

### Post by Kevin h II on 2015-08-21
I have resolved the issue by swapping my sata connections and the other connection from my harddrives and it loads linux then shows GRUB with windows xp load so it worked! now may a moderator please close the thread

EDIT: i didnt see the post above but i disabled raid when i got this desktop its just something im not gonna step into unless i have the time and my data backed up.

---

### Post by Bashing-om on 2015-08-21
Kevin h II; Great !

Only YOU may determine that the situation is to your satisfaction and you are the one to mark the thread as "solved".
1st post -> thread tools
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

