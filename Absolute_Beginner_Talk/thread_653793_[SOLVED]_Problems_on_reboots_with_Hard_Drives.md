---
title: "[SOLVED] Problems on reboots with Hard Drives"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Emmett on 2007-12-30
Hello all

My computer dual boots with Vista and I also have 2 drives that I share for file storage through Samba, These drives are NTFS in structure.

sda1 = a SCSI drive called My-Music
sde1 = a sata drive called All-files

The problem is every reboot of this PC for some reason the hard drives seem to change order as far as BIOS is concerned. I then have to go into system settings hard drives to fix everything. This only happens in Kubuntu 7.1 (Gutsy). In Vista everything remains the same and I share them with my wife's PC and my third PC.

The relevant lines in Fstab is as follows:

# Mount Points for My Servers Hard Drives
/dev/sda1 /My-Music auto user,auto,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sde1 /All-files auto user,atime,auto,rw,nodev,noexec,nosuid 0 0

Any Ideas welcome.

Emmett

---

### Post by phidia on 2007-12-30
What error or message are you getting at boot? I think it would be helpful to know the specific output to attempt troubleshooting. I've had as many as 5 (five) HD's in a system including combinations of IDE & SATA without problems. Unless there is a drive malfunction the bios order shouldn't change.

---

### Post by Emmett on 2007-12-30
Phidia

The 2 Drives that contain Linux and Vista always seem to boot properly. The other drives in my system (of which I use 2 of 3 to share files) seem to have this problem. 

The only error I get is from say my wifes pc or my third pc that they can not connect to the shared drives. I then have to go in and straighten them out everything is fine until the next time I reboot. the only change I have to do is to rename the drives as sdc1 from sdd1.

 I just tried another reboot and everything is fine but I shut this PC off every night as I do not have a need to run it all night or during the day when I am at work..

Is it possible to have Kubuntu boot to a Device Identifier number and how could someone set that up?

Maybe a reload of Linux would fix this?

Thanks
Emmett

---

### Post by Emmett on 2007-12-30
Hello again

Here is two screen shots that show the problem I am having.

Snapshot 3 shows all is well

Snapshot 1 Shows the problem after a reboot.

Any Ideas welcome

Emmett

---

### Post by autocrosser on 2007-12-30
You might try refering to the drives by UUID instead of /dev/sdx--UUID is the new accepted standard--It takes a bit more work to define the drives that way...

1. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
     as in--sudo /sbin/dumpe2fs /dev/sda2 | grep UUID

2. as root user (gksudo gedit /etc/fstab) modify your drive id's--look at mine---

#/etc/fstab: static file system information.
#
# <file system>                    <mount point>         <type> <options>                       <dump>  <pass>
proc                                      /proc           proc  defaults                           0       0
#/dev/sdb1
UUID=906697de-7cef-469f-a1ae-d1a6cd979594 /               ext3  defaults,errors=remount-ro,noatime 0       1
# /dev/sdb6
UUID=c08bbd93-530f-4a52-b165-7d9fb7141db6 /home           ext3  defaults,noatime                   0       2
#/dev/sda1
UUID=606910ae-25d4-4340-8253-e3ad4379810c /mnt/Gutsy      ext3  defaults,noatime                   0       2
#/dev/sda3
UUID=0bace90c-89f6-44b2-a810-1f8c0d563e4d /mnt/GutsyHome  ext3  defaults,noatime                   0       2
#/dev/sda4
UUID=82848829-21fe-4926-a694-c08cea850dd8 /media/Storage  ext3  defaults,noatime                   0       2
#/dev/sdb3
UUID=2cee244e-880b-47a8-b0f6-82a719b05bcc /media/Storage1 ext3  defaults,noatime                   0       2
#/dev/sdb5
UUID=38b1f24d-d3ac-4f49-b8e0-7911f355fd29 /media/Storage2 ext3  defaults,noatime                   0       2
#/dev/sda2
UUID=51fde129-2166-43b3-8363-92a5dcfd1622 none            swap  sw                                 0       0
/dev/scd0                                 /media/cdrom0   udf,iso9660 user,noauto                  0       0
/dev/scd1                                 /media/cdrom1   udf,iso9660 user,noauto                  0       0
/dev/fd0                                  /media/floppy0  auto  rw,user,noauto                     0       0 

This is a non-moving point for all of your drives & the recommended way to have both your /boot/grub/menu.lst & your /etc/fstab

---

### Post by Emmett on 2007-12-30
Thanks

I will give it a try. It looks like a better way. Will let everyone know if it works.

Thanks
Emmett

---

### Post by Emmett on 2007-12-30
Autocrosser

All I get is the following Error on all drives exept the one containing Kubuntu.

emmett@Kubuntu:~$ sudo /sbin/dumpe2fs /dev/sde1 | grep UUID
dumpe2fs 1.40.2 (12-Jul-2007)
/sbin/dumpe2fs: Bad magic number in super-block while trying to open /dev/sde1
Couldn't find valid filesystem superblock.

Does Linux need to format the drive? I believe these drives were first installed by Vista.

Thanks

Emmett

---

### Post by autocrosser on 2007-12-30
Hmmmm--- are they formatted as NTFS?

---

### Post by Emmett on 2007-12-30
Yes they are. All three of the problem ones.

Do I need to repartition  them and redo them as ext3 drives as in your example?

---

### Post by autocrosser on 2007-12-30
My bad---for NTFS you need to do like:

/dev/sda1   /media/windows ntfs defaults,nls=utf8,umask=007,gid=46  0  1

Instead of:
# Mount Points for My Servers Hard Drives
/dev/sda1 /My-Music auto user,auto,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sde1 /All-files auto user,atime,auto,rw,nodev,noexec,nosuid 0 0

Look thru the HowTo section for more info---you still need to use UUID's for the linux-formatted sections.

The reasoning is going from generic descriptions to specific descriptions.

---

### Post by autocrosser on 2007-12-30
Here's the guide I was thinking of:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=ntfs+mount](http://ubuntuforums.org/showthread.php?t=283131&highlight=ntfs+mount)

---

### Post by Emmett on 2007-12-30
Autocrosser thank you.

I used the following two lines and have since rebooted fine:

# Mount Points for My Servers Hard Drives
/dev/sda1 /My-Music ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/sde1 /All-files ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

Also the link you gave me may be helpful for reading later on. I may repost but if you could answer one more question would I be better of using ext3 for my servers hard drives? I could back them up one at a time and repartition.

Thanks again 

Emmett

---

### Post by autocrosser on 2007-12-30
As far as future use--If you are moving more to Linux I would convert to EXT3. There is a extension for Windows (I can't remember the link--I would Google for EXT2/3 for Windows).  EXT3 is a journaled filesystem & is very tolerant as to error-repair.

Edit: Found the link:   [http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/](http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/)

---

### Post by Emmett on 2007-12-30
If any one follows this post I thought I would update it.

I converted my hard drives to ext3 and changed my fstab file to:

# Mount Points for My Servers Hard Drives
UUID=a3518ef4-8cf7-4f72-99e9-ed2843280a4d /My-Music ext3 nouser,defaults,noatime,auto,rw,dev,exec,suid 0 0
UUID=640c1508-ed8c-4537-9b80-f9357619a7a8 /All-files ext3 nouser,defaults,noatime,noauto,rw,dev,exec,suid 0 0

As I said above I thought I would update this. Also I know of the difference in the lines but it works as is from all PC's. If I enable the /All-files drive to auto I can not use the drive from any PC  including Kubuntu and I will eventually fix this as well. I have had enough fun (learning) for the night.

It is for people like Autocrosser helping out that I am learning Linux as I go.

Emmett

---

### Post by autocrosser on 2007-12-30
You're welcome---Linux means to help one another--I was once in your shoes & others helped me--so I contribute to the community by beta-testing & helping others help themselves.

:popcorn:

---

