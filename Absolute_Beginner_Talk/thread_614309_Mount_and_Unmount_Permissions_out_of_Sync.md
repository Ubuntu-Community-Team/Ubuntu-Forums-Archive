---
title: "Mount and Unmount Permissions out of Sync"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Kwag on 2007-11-15
I have been using Ubuntu for about 10 months now.  It has been an interesting ride.  No OS is perfect, I am still dual-booting with Windows XP (I will NEVER buy VISTA), but I am enjoying Ubuntu more  than windows mostly because of the control and security it gives me

Anyway, I usually like to research things on my own, but I have come across something that is strange, to me at least.  There is probably a simple answer.  Anyway,  I have an NTFS partition represented by /dev/sda2.
I wanted to be able to mount this partition without invoking root privileges (no sudo).  So, I edited my /etc/fstab file and replaced "nouser" with "user" for the /dev/sda2 entry.  

As a result, I was able to execute "mount /dev/sda2" just fine, as expected.  

However, when I try to unmount the partition "umount /dev/sda2" I get the following error: 

umount: /dev/sda2 mount disagrees with the fstab

I am pretty sure that this was the same error I was getting when I tried to do "mount /dev/sda2" BEFORE I did the /etc/fstab replacement mentioned above.  

Any help would be appreciated.  Following is the content of my /etc/fstab.  Thanks in advance.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9f2a8007-547a-48ab-927e-7ecc8e927b5d /               ext3    defaults,noatime,errors=remount-ro 0       1
# /dev/sda6
UUID=754b576d-78a7-4256-8861-2652b3458da9 /home           ext3    defaults,noatime        0       2
# /dev/sda1
UUID=07D5-0104  /media/sda1     vfat    ro,suid,dev,exec,noauto,nouser,async,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=D6A48667A48649C7 /media/sda2     ntfs    ro,suid,dev,exec,noauto,user,async,utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    ro,suid,dev,exec,noauto,nouser,async,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=cb00d736-5fd0-422a-993d-9da95c696f45 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by charleseddy on 2007-11-15
Hmm . . . I'm not the be-all, end-all of experts, but the simplest solution is to quickly back up your data and move to 7.10.  Not only is it a quick and nearly flawless OS, but it has native NTFS support.  Give it a try and see; bet you don't even have to mount it manually.

ce

---

### Post by Kwag on 2007-11-15
Well, 

I don't think that upgrading my current Ubuntu installation would necessarily solve this problem would it?

In any case, I am holding out for the next version ("Hardy Heron" I think it is called) which is going to be a long term stable release.  That seems like an optimal time to upgrade.  I am worried that Ubuntu is starting to get too bloated.  Do the newer versions really perform faster than the older versions?

---

### Post by charleseddy on 2007-11-15
Fortunately, 7.10 is lightning, even over 7.04, which was faster than 6.10.  They get so fast it's ridiculous.  I think an improvement is that, recently, they've began to take advantage of dual core and hyper-threading processors, which helps.

I know there's a better time to upgrade, but seriously . . . before 7.10, you can't expect NTFS to work right.  I'm sure there exist very complex workarounds for what you can do, but downloading the disk and installing would be the most simple and effective means.  NTFS-3g, the driver that runs NTFS read-write capabilities, has been unstable before now.  You have to expect that there will be slowdowns if you don't have the latest version.

Unfortunately, I--as a non-expert, but very experienced user and programmer--can only suggest an upgrade.  It's not difficult and takes less than an hour, even with sufficient data transfer (i've done it in less, with about 250 gigs of information on a 250GB 7200 RPM IDE drive and an external USB 2.0 7200 RPM seagate).  It's a quick and easy solution which, while it seems like a chore, would take less time than what you've spent on the forums trying to figure out this simple issue.  I know it seems like a lot of work to reload, but it's easier to get it over with, in my opinion.  But you can wait for more expert advice, if you please.  Good luck, ce.

---

