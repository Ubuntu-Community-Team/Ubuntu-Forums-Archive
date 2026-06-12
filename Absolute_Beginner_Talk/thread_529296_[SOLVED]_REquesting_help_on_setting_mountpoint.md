---
title: "[SOLVED] REquesting help on setting mountpoint"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-08-19
Hi all:  I could use some help setting the mount point on a second hard drive I am adding.  I am in the process of adding a second drive to my box.

Running Ubuntu 7.04 (Fiesty Fawn). The original (first) drive is 20GB. The added (second) drive is 500GB.  Both are ext3 filesystems.

I have installed the new hard disk, formatted, partitioned, and am trying to make its mountpoint. Looked around and found a document explaining exactly how to do this at [https://help.ubuntu.com/community/In...gANewHardDrive](https://help.ubuntu.com/community/In...gANewHardDrive)

The point where I am stuck is here in the document.  It says:

> Now we can mount the drive to the mount point.
    * sudo mount /dev/hdd1 /media/mynewdrive        
If all goes well, you should be able to use your drive at the mount point you chose. 

All didn't go well.  I got the following error, and don't know what to do from here.

> m9ke@m9ke-desktop:~$ sudo mount /dev/sdb /media/bigdrive
Password:
mount: you must specify the filesystem type
m9ke@m9ke-desktop:~$ 

You can see in the above that I used "bigdrive" instead of "mynewdrive" as suggested in the document, but I don't see how that could cause problems.

Does anyone know how I should proceed from here?

Thanks,
m9ke

---

### Post by jtraub on 2007-08-19
```
sudo mount /dev/sdb1 /media/bigdrive

```

---

### Post by m9ke on 2007-08-19
Yikes!

m9ke@m9ke-desktop:~$ sudo mount /dev/sdb1 /media/bigdrive
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

m9ke@m9ke-desktop:~$

---

### Post by taurus on 2007-08-19
```
sudo mount -t ext3 /dev/sdb1 /media/bigdrive
```

Otherwise, post

```
sudo fdisk -l
```

---

### Post by m9ke on 2007-08-19
Thanks Taurus.  Identical error results from your first suggestion.  Posting result of your second suggestion.  As you will see I have two hard disks installed.

m9ke@m9ke-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2392    19213708+  83  Linux
/dev/sda2            2393        2501      875542+   5  Extended
/dev/sda5            2393        2501      875511   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
m9ke@m9ke-desktop:~$

---

### Post by taurus on 2007-08-19
Is there anything on /dev/sdb1?  Maybe you need to reformat it again.

```
sudo mke2fs -j /dev/sdb1
sudo mount -t ext3 /dev/sdb1 /media/bigdrive
df -h
```

---

### Post by m9ke on 2007-08-19
Writing inode tables now.  Will post result.

---

### Post by m9ke on 2007-08-19
It looks like it formatted successfully.  Below is the output.  

Can you tell by looking if I have completed the installation, or should I do something to check?

m9ke@m9ke-desktop:~$ sudo mke2fs -j /dev/sdb1
Password:
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61063168 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

---

### Post by taurus on 2007-08-19
Everything is looking good.  Now, mount it and see what happens.  Should work now.

---

### Post by m9ke on 2007-08-19
Taurus, thanks very much.

It appears to have worked.  Here is the output of the original command you gave me.  I am going to reboot the box to see what happens then.

m9ke@m9ke-desktop:~$ sudo mount /dev/sdb1 /media/bigdrive
m9ke@m9ke-desktop:~$

---

### Post by yellowband on 2007-08-19
you could put the mount info in /etc/fstab to avoid having to remount the drive evry time you boot your os:

edit /etc/fstab

add a line like this:

/dev/sdb1     /mount/yournewdrive     ext3      defaults     0     0

where /mount/yournewdrive is any folder you make to be a place where your drive is mounted. emember to make that folder first though.

---

### Post by taurus on 2007-08-19
> **yellowband said:**
> you could put the mount info in /etc/fstab to avoid having to remount the drive evry time you boot your os:

edit /etc/fstab

add a line like this:

/dev/sdb1     /mount/yournewdrive     ext3      defaults     0     0

where /mount/yournewdrive is any folder you make to be a place where your drive is mounted. emember to make that folder first though.

Actually, I would edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/bigdrive   ext3   defaults   0   1
```
Then, I would change the ownership of /media/bigdrive from root to your login name, m9ke, so you can write to it without using sudo.

```
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media
```

---

### Post by m9ke on 2007-08-19
Booting problems now.
IDE devices are:
Primary Master: 20 GB drive, this drive contains Fiesty
Primary Slave:  500 GB drive, the new one just formatted

Secondary Master CD RW drive
Secondary Slave:  CD drive

Tried to boot the box two ways:

**First with these BIOS settings:**
Primary Master: 20 GB drive, this drive contains the OS-autodetect
Primary Slave:  500 GB drive, the new one just formatted-autodetect

Secondary Master CD RW drive-autodetect
Secondary Slave:  CD drive-autodetect

In this first case, the box appears to be trying to boot off one of the CD drives.  I gets to a screen describing the drive (not in BIOS).  I get a command prompt at the bottom of this screen. Note that the box has not yet booted Ubuntu.

So I tried it differently:

**Second with these BIOS settings:**
Primary Master: 20 GB drive, this drive contains the OS-autodetect
***Primary Slave:  500 GB drive, the new one just formatted-change autodetect to none in BIOS***

Secondary Master CD RW drive-autodetect
Secondary Slave:  CD drive-autodetect

In this second case, the box boots into Ubuntu, but only after several minutes.

Before formatting partitioning and setting mount point the second new drive was physically installed in the box for a day or two with no booting problems.  BIOS settings were as described in the first case above.

Stumped!!

---

### Post by m9ke on 2007-08-19
Long booting problem solved.  Marking [Resolved]

Went into BIOS advanced settings and made the following changes:
First boot device:  was CD ROM, left as is
Second boot device: was HDD1; changed to HDD 0
Third boot device: was HDD0; changed to HDD1

What I think might have caused the problem:  previous settings made the box try to boot from the new drive (HDD1), which is big and contains no OS.  It then went to the old drive, which contains Fiesty (HDD 0) and booted.  Thus it took several minutes to boot.

The new settings mean that the box now looks first at the CD ROM for the OS, doesn't find it, and then goes straight to the old drive which contains Fiesty (HDD 0)

I am writing this up with the idea that somebody might have a similar problem and find out how I fixed mine by searching the forum.  Disclaimer:  I am no where near an expert on this stuff, and this info is just what I did and my interpretation of it.  A real expert could come along and touch up my description, for those who might find this and get misled by what ever mistakes I made.

Also thanks taurus and yellowband for your suggestions re automounting and changing ownership.  Did that and it worked.

---

