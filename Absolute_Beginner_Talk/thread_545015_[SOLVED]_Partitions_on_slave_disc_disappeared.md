---
title: "[SOLVED] Partitions on slave disc disappeared"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by multi-os-guy on 2007-09-07
Hi,

I did a clean install of Ubuntu last night, and after getting my display drivers and Java SDK setup I went to access some files on my slave disc, only to find no reference to it in the file explorer.  So I opened Gnome Partition Manager?Editor? and viewed my disc, only to find that it sits at unallocated.  BUT when I boot in Windows (sorry, I know some of you consider this a swear word) I can access all of my files from these partitions, so I'm guessing there's nothing wrong with the partitions themselves.

How can I make Ubuntu recognise my partitions, if the Gnome Partition Manager?Editor? says they don't exist?  Maybe I can do ANOTHER fresh install and it will fix it?  :D

Then again, if I do another fresh install, I have a feeling my computer will get up and walk out on me. :)

I have read some instructions on manually setting up fstab entries etc, but surely not even that will work if my partitions don't exist!

Thanks heaps,
Daniel

---

### Post by banewman on 2007-09-07
Are there any entries in fstab for those partitions?

---

### Post by multi-os-guy on 2007-09-07
I'll reboot and check...

---

### Post by multi-os-guy on 2007-09-07
Yes, I have one partition actually working.  The others don't appear.  It' s a bit of a problem because I have several distro's installed on that drive and I can't access them.  Not that I could create a new Grub entry for them anyways...but if I could access their partitions I could take the entries from their menu.lst files.  Any ideas?  Perhaps if I just add a few 'random' entries (best guess approach) into my fstab file?  I guess it can't really hurt, and I can always just remove them if they don't work?

---

### Post by vanadium on 2007-09-07
To obtain more specific help, you might want to post the output of the following commands here:

sudo fdisk -l

This lists all the drives and partitions that your system "sees"

mount

This lists all the drives that are actually mounted.

Try

sudo mount -a

This reloads your fstab. If there is no error message, then your fstab is fine. If there is an error message, then one of the partitions indeed is not mounted because of some error (wrong syntax, inappropriate option, ...

---

### Post by multi-os-guy on 2007-09-08
Hi,

I put the output below.  Sorry about the late reply, my internet has been down since I tried to install it on Ubuntu last night.  I think I can detect the problem, but how can I fix it.

(Yes, you're going to look at it and go, "You're crazy, man!"  Who needs that many partitions?  Short answer:me)

USING THE FDISK COMMAND:

root@daniel-desktop:/home/daniel# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825        7012    25600000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3            7013        9729    21824302+   5  Extended
/dev/hda5            7013        9598    20772013+  83  Linux
/dev/hda6            9599        9729     1052226   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           2       24774   198989122+   5  Extended
/dev/hdb2   *       12750       21673    71682030    b  W95 FAT32
/dev/hdb3           21674       23497    14651280   83  Linux
/dev/hdb5               2       12749   102398278+   7  HPFS/NTFS
/dev/hdb6           23498       24774    10257471   83  Linux

Disk /dev/sde: 203.9 GB, 203928109056 bytes
54 heads, 41 sectors/track, 179899 cylinders
Units = cylinders of 2214 * 512 = 1133568 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       92503   102399984    7  HPFS/NTFS



USING THE MOUNT COMMAND:

daniel@daniel-desktop:~$ mount
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/disk/by-uuid/94A42823A42809F6 on /media/hda1 type fuse (rw,nosuid,nodev,noatime,allow_other)
/dev/disk/by-uuid/C0646CB1646CABBA on /media/hda2 type fuse (rw,nosuid,nodev,noatime,allow_other)
/dev/hdb5 on /media/100GB type fuse (rw,nosuid,nodev,noatime,allow_other)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by vanadium on 2007-09-08
Your mount command reveals that only hdb5, an ntfs partition, is mounted. This, it is the only one for which you would find reference in your file system. You can reach it through /media/100GB

My guess is that the other partitions are not included in /etc/fstab (your re-install didn do this for one or another reason). Post your /etc/fstab here so we can make sure. If they are not in there, then we add them ourselves. If they are already in there, then something is wrong (fstab syntax, partition, ...)

To post your /etc/fstab, issue the command

cat /etc/fstab

---

### Post by multi-os-guy on 2007-09-08
OK, I ran the 'cat' command and got the following in my terminal.  Thanks so much for your help, I appreciate it.  I don't think the entries are there.  I've tried copying the last entry (for my 100GB disk (no prize for guessing how big it is), and then changing the hd? bit and the name, but no luck. 

THE OUTPUT OF CAT /ETC/FSTAB

daniel@daniel-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=0cabbb38-4c38-4bf5-869d-601f79f796bb / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=94A42823A42809F6 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda2 :
UUID=C0646CB1646CABBA /media/hda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=d69ae83b-a0b7-409e-a11a-3853b2fbbe41 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb5 /media/100GB ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by vanadium on 2007-09-08
Then the solution will be simple. Yu just need to (1)create mount points for them and (2) add them to /etc/fstab

/dev/hdb2 * 12750 21673 71682030 b W95 FAT32
/dev/hdb3 21674 23497 14651280 83 Linux
/dev/hdb5 2 12749 102398278+ 7 HPFS/NTFS
/dev/hdb6 23498 24774 10257471 83 Linux


(1) create the mount points. This means: create empty directories where we will mount the drives.

sudo mkdir /media/hdb2
sudo mkdir /media/hdb3
sudo mkdir /media/hdb6

* load /etc/fstab in your editor
gksudo gedit /etc/fstab

* Add entries for the partitions, for example:
/dev/hdb2 /media/hdb2 vfat iocharset=utf8,umask=000 0 0
/dev/hdb3 /media/hdb3 ext3 defaults 0 2

I am not sure of the file type of your Linux partitions (those marked "Linux" in the output of "sudo fdisk -l". You will have to make sure yourself using the vol_id command. For example. to learn about your /dev/hdb3 partition, issue the command "sudo vol_id /dev/hdb3".

I will illustrate with my (only) partition:

$ sudo vol_id /dev/sda1
Password:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=113d4806-2eb3-492a-bf81-de560d9ed70d
ID_FS_LABEL=usd_data
ID_FS_LABEL_SAFE=usd_data

You see the file type given here as "ext3". This command also provides the UUID. Therefore, instead of mounting the device name, you might mount by UUID instead as recent Ubuntu distributions do. The advantage of that is that UUIDS do not change, while /dev references might change if you add or delete partitions.

Thus, while I could mount my drive with

/dev/sda1 /media/sda1 ext3 defaults 0 2

it is preferred to mount it using

#entry for sda1
UUID=113d4806-2eb3-492a-bf81-de560d9ed70d  /media/sda1 ext3 defaults 0 2

I added the comment #entry for above so that later you can easily see that this was the sda1 partition.

I advice you to add each partition one at a time. When you added one, reload fstab using the command

sudo mount -a

If you see an error message, the mounting for the line you added did not work out right (typing mistake, forgot to make mount point, ...). If you don't see an error, the partition should be mounted correctly and be visible in nautilus (or using ls /media/hda2, where you obviously replace /media.hda2 by the actual reference).

Some remarks:
(1) do only mount these partitions that you use all the time in /etc/fstab. If you just want to access the partition once, you are better of mounting it only when you need it.
(2) you won be able to write to any of your partitions. Indeed, you will need to set appropriate permissions to give yourself as a user write access. If needed, we can address that once you achieved mounting the partitions.

---

### Post by multi-os-guy on 2007-09-08
Thankyou.  I will attempt it right away.

---

### Post by multi-os-guy on 2007-09-08
Thanks to your instructions I can now access all of my partitions.  I will need to set up write access ONLY to the music drive which is the hdb2 drive.  I will also comment the Vista partition out of fstab because I don't need to access it (it contains no personal files because I don't use it)  I could also comment out the other Linux distro's couldn't I? 

I have just two problems left, really.  Now that I can access my files inside Ubuntu, how do I (sin of all sins) boot one of my other distros?  I've attached my GRUB, but I can well understand if you don't want to touch it.  After all, it is a Ubuntu forum...  And the other problem is writing to my FAT32 drive...any help would be appreciated, and thanks heaps for the previous instructions.

Regards,
Daniel

---

### Post by vanadium on 2007-09-08
The problem of the (disappearing) folders has been solved (at last), and /etc/fstab is less of a secret for you now. For additional issues, I recommend you open a new thread - one issue = one thread.

Using the "Thread tools" link, you can mark this thread as "SOLVED".

---

### Post by multi-os-guy on 2007-09-08
Thankyou Vanadium.  I really appreciated your help.

---

