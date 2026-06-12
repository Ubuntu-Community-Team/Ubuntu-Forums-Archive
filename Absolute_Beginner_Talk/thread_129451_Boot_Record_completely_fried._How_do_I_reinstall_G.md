---
title: "Boot Record completely fried. How do I reinstall GRUB / access ubuntu?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-02-13
Main system:

SATA 300GB: /dev/sdb (mounted as /)
SATA 160GB: /deb/sda (NTFS windows drive, mounted under media)

Somehow, I screwed something up while copying files to my windows drive from the windows install disk (was in recovery mode, and I didn't mess with my MBR.) Afterwards, my computer would automatically load the windows bootmanager, booting me into my win2k install, wtf. I could get to grub if I booted off my SBM floppy, and the ubuntu boot process would start, but it would error after mounting the root drive. I didn't TOUCH the drive, although in windows I installed an ext2 fs driver, whihc didn't work. My ubuntu drive has a lot of data on it and I don't want to lose any of it. At the very least, how do I get my bootloader back? I don't have the livecd, although this computer I'm posting from has a floppy drive. Is there any way I can write a bootable grub floppy and use *that* to boot my ubuntu install, so I can at least see what the error message is and google for help? Post any suggestions you may have.

---

### Post by Adrian on 2006-02-13
Maybe this thread will help:
[http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by wr0x2 on 2006-02-14
Thanks, but when I follow the instructions specified in the second post, everything works until I get to the point where I mount my drives as root. When I do this, I get an error. I checked /var/log/messages, and I saw some interesting things like the module for ext2 not being available among other things. How can I recover my existing system? I most certainly do not want to do a reformat / reinstall or even reinstall at all.

EDIT: In particular, the errors that caught my eye were:
```

FATAL: Module ext2 not found.
FATAL: Module lvm_mod not found.

```
and
```

mount: Mounting /dev/discs/disc1/part1 on /target failed: Input/output error

```
Also, maybe not being able to mount my fs here has something to do with me not being able to mount root fs on the regular boot process? Ideas as to whether these two things are connected?

---

### Post by wr0x2 on 2006-02-14
*bump*

---

### Post by towsonu2003 on 2006-02-14
try this one? wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows

---

### Post by wr0x2 on 2006-02-15
OK, I downloaded the livecd and it looks like I have a bigger problem.  It seems my whole partition table is messed up. How can I get more info on the drive's status? My windows drive will mount and identifies the FS as NTFS, but although I can mount my second drive with ubuntu, I cannot enable it for access.

EDIT: WTF, this is even more confusing. I open up my /deb/sdb (the one with ubuntu that I can't access) with fdisk, and it correctly identifies the main partition as ext3! What's going on here?

---

### Post by wr0x2 on 2006-02-15
All right, to help you guys out some more, here's the output of dmesg | tail after I try to mount the drive on the cmd line:

```

root@ubuntu:/home/ubuntu/Desktop# dmesg | tail
[4296979.813000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4296979.814000] EXT3-fs: group descriptors corrupted !
[4296983.504000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4296983.505000] EXT3-fs: group descriptors corrupted !
[4297120.141000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297120.142000] EXT3-fs: group descriptors corrupted !
[4297122.949000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297122.949000] EXT3-fs: group descriptors corrupted !
[4297125.899000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297125.900000] EXT3-fs: group descriptors corrupted !

```

If this means unfixable data corruption (how did that happen?) then is there any way I can access my files to back them up before I reformat?

---

### Post by towsonu2003 on 2006-02-15
did you manage to recover grub? 
[QUOTE=wr0x2]OK, I downloaded the livecd and it looks like I have a bigger problem.  It seems my whole partition table is messed up. How can I get more info on the drive's status? My windows drive will mount and identifies the FS as NTFS, but although I can mount my second drive with ubuntu, I cannot enable it for access.[/quote]
I could not really understand the problem... ubuntu livecd mounts the ntfs but cannot access it? or something else? 

also, please post the output of
```

sudo fdisk -l
cat /etc/fstab
sudo mount -a
mount | sort
df -h
```
[QUOTE=wr0x2]
EDIT: WTF, this is even more confusing. I open up my /deb/sdb (the one with ubuntu that I can't access) with fdisk, and it correctly identifies the main partition as ext3! What's going on here?[/QUOTE]
yep, I have no idea what your problem currently is... :-k  are you unhappy bc ubuntu mounts your ext3 correctly? ;)

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=wr0x2]All right, to help you guys out some more, here's the output of dmesg | tail after I try to mount the drive on the cmd line:

```

root@ubuntu:/home/ubuntu/Desktop# dmesg | tail
[4296979.813000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4296979.814000] EXT3-fs: group descriptors corrupted !
[4296983.504000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4296983.505000] EXT3-fs: group descriptors corrupted !
[4297120.141000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297120.142000] EXT3-fs: group descriptors corrupted !
[4297122.949000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297122.949000] EXT3-fs: group descriptors corrupted !
[4297125.899000] EXT3-fs error (device sdb1): ext3_check_descriptors: Inode bitm ap for group 384 not in group (block 2147483647)!
[4297125.900000] EXT3-fs: group descriptors corrupted !

```

If this means unfixable data corruption (how did that happen?) then is there any way I can access my files to back them up before I reformat?[/QUOTE]
This is more serious I think. Check out this link: [http://www.die.net/doc/linux/man/man8/e2fsck.8.html](http://www.die.net/doc/linux/man/man8/e2fsck.8.html)

When I googled for your error, it looked like a problem with superblocks (??). And I have no idea how to help with that stuff... 

you might wanna post a new thread for this error, posting the error and the exact steps you took until this happened, on how to salvage your information from that partition or the partition itself... there are already 8 posts in here and the title is grub, so probability of people knowing more about partitions looking at this post is extremely low...

---

### Post by wr0x2 on 2006-02-15
```

root@ubuntu:/home/ubuntu/Desktop# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36103   289997316   83  Linux
/dev/sdb2           36104       36481     3036285    5  Extended
/dev/sdb5           36104       36481     3036253+  82  Linux swap / Solaris

```
```

root@ubuntu:/home/ubuntu/Desktop# cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
root@ubuntu:/home/ubuntu/Desktop#

```
sudo mount -a has no output
```

root@ubuntu:/home/ubuntu/Desktop# mount | sort
/dev/mapper/casper-snapshot on / type auto (rw,noatime)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /home/ubuntu/Desktop/Windows type ntfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
usbfs on /proc/bus/usb type usbfs (rw)

```
```

root@ubuntu:/home/ubuntu/Desktop# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.3G  665M  66% /
tmpfs                 507M  4.0K  507M   1% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
tmpfs                 507M   24K  507M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev
/dev/sda1             150G  103G   47G  69% /home/ubuntu/Desktop/Windows
root@ubuntu:/home/ubuntu/Desktop#

```

I never did get grub installed, I need to fix whatever is wrong with my /dev/sdb1 partition first. If it wasn't clear from above, I can't get that drive to mount.

---

### Post by towsonu2003 on 2006-02-15
one more output: 
sudo mkdir /randomdir
sudo mount /dev/sdb1 /randomdir -t ext3 -r
ls /randomdir (only if the second command did not give output)

assuming that sdb1 is ext3. 

I'm not very hopeful that I will be able to solve this though...

Edit: just edited commands one and two

---

### Post by wr0x2 on 2006-02-15
```

root@ubuntu:/home/ubuntu/Desktop# sudo mount /dev/sdb1 /uext3 -t ext3 -r
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

Same output as before.

---

### Post by towsonu2003 on 2006-02-15
yea
I was hoping for the best
I think you should open a new thread... Have no idea how to solve that. You might wanna include the outputs you gave here along with the steps you took bf this happened (I think it is your first post, kinda~)

sorry, couldn't help much....

---

### Post by steve.horsley on 2006-02-16
This is bad. It looks like windows has fried your partition for you. It might be interesting to use cfdisk or fdisk to change the partition type to vfat or ntfs and then see if you can mount it. If so then windows has formatted it. Make sure you note the original type number so you can change it back.

The equivalent of chkdisk would be:
fsck.ext2 /dev/sdb1
but i'm not sure if even that can undo the damage.

STeve

---

### Post by Adrian on 2006-02-16
The Windows installer has destroyed ext3 partitions for me, even though I told it NOT to touch other paritions than its own.

An fsck always made things work again.

---

### Post by barrosz on 2006-02-16
Hi im a newbie and all but if you just want to backup stuff from xp try [this app]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

---

