---
title: "Mounting a Windows disk."
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by xmastree on 2005-05-13
Ok, this isn't really an ubunto specific question, more of a general linux question...

I have a Win XP system, and I've insyalled ubuntu on a removable disk, connected as primary slave. I can select this at boot up, and it works fine. Switch on and do nothing, WinXP. switch on and hit escape at the right moment, I get a menu and can select the slave, and linux boots.

I want to mount the secondary partition of the windows disk (which I use for data), but I'm having trouble making it available to users other than root. 
I've created a mount point /mnt/windisk and I've created a group, windisk, and that directory is owned by windisk but only if the disk isn't mounted.

I've added the following to /etc/fstab:

/dev/hda5	/mnt/windisk	ntfs	ro	0	0

The drive mounts ok, but only root can read it.
If I unmount it, I see this:

root@ubuntu:/mnt # ls -l
total 4
drwxr-xr-x    2 root     windisk      4096 2005-05-13 05:20 windisk

So all can access that directory. However, when I mount it

root@ubuntu:/mnt # mount /dev/hda5 /mnt/windisk

The permissions change.

root@ubuntu:/mnt # ls -l
total 4
dr-x------    1 root     root         4096 2005-04-16 19:54 windisk

How can I make it so that members of the group 'windisk' can read it when it's mounted? I've tried (as root) changing the permissions after it's mounted, but it doesn't change...

And what's with that date? unmounted it's may 13, correct. Mounted it changes to april 16...


 ](*,)

---

### Post by bored2k on 2005-05-13
Replace your custom line in /etc/fstab for this one:
/dev/hda5 /mnt/windisk  ntfs    umask=0222      0       0

And when you're mounting it manually, use this command:
sudo mount /dev/hda5 /mnt/windisk -t ntfs -o umask=0222

That **will** fix things.
More info. on [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

-- Another useful command:
df -h : this will report mounted filesystems and their disk usage.
sudo fdisk -l : will show you the detected partition tables [useful for knowing what hda* you're going to work with].


Good luck with ubuntu,
Rafael.

---

### Post by xmastree on 2005-05-13
Thanks. I'm about to go home for lunch, I'll try that and report back.


If the damn thing will boot, but that's another story...

---

### Post by bored2k on 2005-05-13
Lunch ? wow your like waaaay on the other side of the planet. I'm in the caribbean it's 00:38, wich means by the time you come back I'll be zZzZz mode.

---

### Post by xmastree on 2005-05-13
Yep. I sent that at 12:14 local time. It's 2:05 now...

Anyway, you'll be pleased to know that it worked!  :) 
But then you knew it would, didn't you?

Thanks again.

---

### Post by BKSea on 2005-06-01
I have followed the instructions from above and in the faq.  I did the following:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

and get this message:

mount: /dev/hda1 already mounted or /media/windows busy

Then when I open the file manager and go to the /media/windows folder, nothing is there....

What should I do?

---

### Post by bored2k on 2005-06-01
[QUOTE=BKSea]I have followed the instructions from above and in the faq.  I did the following:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

and get this message:

mount: /dev/hda1 already mounted or /media/windows busy

Then when I open the file manager and go to the /media/windows folder, nothing is there....

What should I do?[/QUOTE]
 Are you sure /dev/hda1 is the right location ?
Type sudo fdisk -l to know what's your right partition.

---

### Post by BKSea on 2005-06-02
Yes it is definately the right one....


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1162     9333733+  83  Linux
/dev/hdb2            1163        1216      433755    5  Extended
/dev/hdb5            1163        1216      433723+  82  Linux swap / Solaris

---

### Post by nosfera2 on 2005-06-02
Hi,

Sorry to jump on your thread, I have a similar question so thought I'd post here rather than creating a new post.

I have 1 SCSI disk which has my Ubuntu 5.04 install. The PC boots from the IDE disk. The IDE disk has a whole bunch of info on there that I amtrying to get to. 

I have read the following:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)
[http://ubuntuforums.org/showthread.php?t=37664](http://ubuntuforums.org/showthread.php?t=37664)
[http://ubuntuforums.org/archive/index.php/t-8007.html](http://ubuntuforums.org/archive/index.php/t-8007.html)

I am trying to mount an extended partition:

my sudo fdisk -l shows the following:
Disk /dev/sda: 4293 MB, 4293632000 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         496     3984088+  83  Linux
/dev/sda2             497         522      208845    5  Extended
/dev/sda5             497         522      208813+  82  Linux swap / Solaris
Disk /dev/hdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 [B]  Device Boot      Start         End      Blocks   Id  System
/dev/hdc2             525        4982    35808885    f  W95 Ext'd (LBA)
/dev/hdc5             525        4982    35808853+   b  W95 FAT32[/B]

I am trying to mount hdc2 and 5, but neither will mount. 
[B]
sudo mount /dev/hdc2 /mnt/win_fat/ -t vfat -o umask=000[/B]
gives me an error message:
[B]mount: wrong fs type, bad option, bad superblock on /dev/hdc2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

dmesg | tail: (I did try to mount it as NTFS, as a matter of interest, hence the NTFS refs in here)
[B]FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hdc2.
NTFS-fs error (device hdc2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdc2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdc2): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hdc5): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdc5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdc5): ntfs_fill_super(): Not an NTFS volume.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hdc2.
[/B]

Any and all suggestions welcome.

---

