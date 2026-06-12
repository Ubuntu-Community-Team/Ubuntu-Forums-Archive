---
title: "restoring grub - confused"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-03-11
Hello,

Here's my situation:

2 Hard Drives.  Originally had windows on 1st HD.  Then installed Ubuntu on 2nd HD.  Ubuntu Grub worked fine.  

Next, I wiped out windows with OpenSuse.  OpenSuse's Grub worked fine.

Now my daughter complains about not being able to play her games, so I want to put windows back on the 1st HD.

I'm currently booted into Ubuntu, on the 2nd drive, and I have used the partition manager on the 1st HD to move a "/spare" partion to the end of the disk.  I hope to keep this partition on the 1st HD during the windows installation to that drive because it contains backup files and data I will need for windows XP and windows software.

So I've got a huge space at the beginning of the 1st HD and the 'spare' partition at the end of the disk -[U] I want to do a trial run of restoring Ubuntu's Grub - this is what I want to use even after WinXP is installed.
[/U]
I figure if I reboot now, I'll have trouble since OpenSuse's Grub has been wiped out.

I've been trying this HowTo: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Here's what I've done, in a root terminal, but I'm not sure what I've accomplished and if it's ok to reboot now.  Note: I altered from the HowTo instructions and did: 

"root (hd1,0)" instead of "root (hd0,1)" since the latter gave me an error.  I assumed I should use the value that was returned by "find /grub/boot/stage1" which was (hd1,0).

```
grub> root
 Possible commands are: root rootnoverify

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```What should I do now?

I'm concerned with this "fdisk -l" output, as it shows that partitions are not in order.  I'm not sure it matters, as this is only a trial run.  But I opened up GParted, and indeed it shows my "spare" partition as /dev/sda1.  Will that cause me problems later, after reinstalling WinXP?

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c5aed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14983       19457    35945437+  83  Linux
/dev/sda2               1       14982   120342883+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7c7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

```

---

### Post by glennric on 2008-03-11
You seem to be in order.  Just install windows to the partition you want.  It seems that is sda2.  Make sure you choose the larger partition to install to.  GParted numbers partitions in the order created, not in the order on the disk by the way.  After you install windows you will have to restore grub.  Then you should be set.

---

### Post by glennric on 2008-03-11
When you created the partitions did you tell gparted to put the spare partition at the end of the disk?

---

### Post by aBitLater on 2008-03-11
> **glennric said:**
> When you created the partitions did you tell gparted to put the spare partition at the end of the disk?

I just moved it around (graphically), and the box that says, "Free Space Following" is "0".

---

### Post by aBitLater on 2008-03-11
> **glennric said:**
> You seem to be in order.  Just install windows to the partition you want.  It seems that is sda2.  Make sure you choose the larger partition to install to.  GParted numbers partitions in the order created, not in the order on the disk by the way.  After you install windows you will have to restore grub.  Then you should be set.

will I have trouble with the current menu.lst file?  (it automatically put in the option for windows on the first go-around, and windows was (hd0,0)
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Still confused about the spare partition being /dev/sda1, and how this will affect the boot entry above - should I change it to (hd0,1) - or does this (hd0,0) entry have nothing to do with /dev/ mappings?

---

### Post by glennric on 2008-03-11
You will have trouble with that if you install windows on /dev/sda2.  Do you have anything on /dev/sda1 yet?  If not, or if you can back it up, you should delete all of the partitions on sda and recreate them.

---

### Post by aBitLater on 2008-03-11
well, I started the winxp install and noticed that the larger partition (the first one, which ubuntu says is /dev/sda2) is labeled as drive F: in the windows setup.  my 'spare' (/dev/sda1) partition is labeled C: in the windows setup.  I don't want that - too awkward for installing windows software later.

So, It looks like I'll have to backup the 'spare' partition (/dev/sda1), then wipe it out and use on big partition for windows....

Thanks for your input.

---

### Post by glennric on 2008-03-11
You should be able to change which one is C: in the windows setup, but if you can backup that is probably better.  You can still recreate the spare partition.  Just make sure when you create the two partitions on /dev/sda with gparted, that you create them in the order you want them on the disk, and have gparted apply the operations at the same time.  Then the first partition on the disk will show up as C: in windows setup.

---

### Post by aBitLater on 2008-03-11
weird!, WinXP setup recognizes my 2nd Disk's (ubuntu) partitions as Disk 0, ID 1 and labels them C:, and F: respectively (F: must be swap or something).

So, when I partition the 1st drive in WinXP setup, it labels it as G: and indicates it is Disk 0, ID 0.

My assumption here, at first, was that Disk 0 meant the 2 disks are on the same controller, and the ID is the number of the actual drives.

I hope I don't get stuck with G: in windows after install... it seems like a lot of windows programs expect to be installed on C: and get goofy if they are not on the 'default' drive.

---

### Post by glennric on 2008-03-11
Most windows programs will install to the default install drive for windows.  If windows installs to G: then most programs will want to do that.  I am not sure about the numbering in the windows setup.

---

