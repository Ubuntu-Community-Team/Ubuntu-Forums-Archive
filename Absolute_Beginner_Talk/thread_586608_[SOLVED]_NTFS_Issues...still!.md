---
title: "[SOLVED] NTFS Issues...still!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by evolushun on 2007-10-22
Pretty annoyed now.  I have tried so many different things to get my drive to be recognized and nothing has helped.  I can see the drive but I cannot do anything with it.  I have installed NTFS Config and that doesn't help.  It keeps telling me that I cannot mount the volume and I do not have windows installed anymore, nor do I want it.  I cant format this drive because it has some irreplaceable pictures and documents on it.  I have had a few people try to help me with this issue but nobody can figure it out.  Can someone please take 10 minutes to work with me on this???  I'm really frustrated and this is the only problem I am having with Ubuntu!

---

### Post by Vansinnesvisan on 2007-10-22
What does it say in the terminal when you manually try to mount it?

Something like:
sudo mount -t ntfs /dev/<yourhard drive> /mnt/<where you want it mounted>

You can display drives and partitions  to find out which drive it is:
sudo  fdisk -l  (lowercase L)
or
sudo fdisk -l | grep NTFS

Make sure the ntfs module is loaded:
lsmod | grep ntfs

---

### Post by evolushun on 2007-10-22
Honestly, I do not know how to mount it.  I didn't type anything like that.  Linux is still very foreign to me but I am trying my best to learn.  I did change the drive to "ro" for read-only and can see the drive on my desktop now.

---

### Post by Qwerty_ on 2007-10-22
When you installed NTFS config, did you then run it?

```
sudo ntfs-config
```

---

### Post by evolushun on 2007-10-22
Yes and it just offers me the choice of enabling write support for external device.  I have it checked and click OK but it still wont let me write to the external drive.  I haven't had any options for where I want to mount this drive nor what I want it called.  Does this help?

---

### Post by ltcolfury on 2007-10-22
I just posted a fix that worked for me last week since I had the same problem.

This is what I did and got it to work.

Uninstall the NTFS-3g and the NTFS -config. Install it through Automatix & reboot. After that it'll mount for you. But what I did was go back into the package manager and install the NTFS-config. (After another reboot it wouldn't mount until I installed the -config which you will find in the Applications/System Tools menu after that installation.)

After that, it worked for me every time. I tried everything else that I found listed on the forums and only this method worked for me.

---

### Post by evolushun on 2007-10-22
How do I install NTFS-3G?  I dont think I ever installed that.

---

### Post by Arwen on 2007-10-22
Probably with > sudo apt-get install ntfs-3g and then > sudo apt-get install ntfs-config

---

### Post by ltcolfury on 2007-10-22
Open up the Package Manager (System/Admin/Synaptic...) and search and type in "ntfs" without the quotes. You will find 2 listings for the ntfs that you will need. (-3g and the -config)

Do you have automatix installed? If you don't you can try and skip that & install it through the package manager. Some people frown on Automatix it but I never had any problems with it.

[www.getautomatix.com/wiki/index.php?title=Installation](www.getautomatix.com/wiki/index.php?title=Installation)

Or use the above process the other poster posted. Both ways will install it.

---

### Post by LibertyShadow on 2007-10-22
Perhaps a live CD would mount the partition.  If you just need to get some vital pictures and documents, I would suggest that you boot from a live CD and try to copy them from the NFTS partition to your linux partition. You could use Knoppix, or an Ubuntu live CD.:KS good luck

---

### Post by evolushun on 2007-10-22
I have both of them installed and I even installed Automatix but still cannot write to that drive.  Am I just royally screwed?

---

### Post by Qwerty_ on 2007-10-22
He would have to install NTFS-config whilst on the live cd though.

This is possible though as I did it when I messed up my Ubuntu system once, and wanted to backup some data to my external drive.

---

### Post by evolushun on 2007-10-22
Since I can see my drive now and can access it, could I pull all my files off of the drive and format it into a FAT32 and place my files back on it?

---

### Post by Qwerty_ on 2007-10-22
I guess you could do that but FAT32 has limitations (cannot have files bigger than 4gb on it)

EDIT: Have you restarted after using ntfs-config?

---

### Post by evolushun on 2007-10-22
Yes, I have rebooted a few times.

---

### Post by evolushun on 2007-10-22
Well, since this is being a pain, what are my options?

---

### Post by logos34 on 2007-10-22
> **evolushun said:**
> Well, since this is being a pain, what are my options?

1. back up and format as fat32 (or ext3 if you no longer have windows).

2. continue to troubleshoot ntfs-3g

Why don't you post a few files so we can see your disk layout:

**sudo fdisk -l**

**cat /etc/fstab**

**mount**

---

### Post by evolushun on 2007-10-22
sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11832    95040508+  83  Linux
/dev/hda2           11833       12161     2642692+   5  Extended
/dev/hda5           11833       12161     2642661   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30400   244187968+   7  HPFS/NTFS


cat /etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=2071d79b-9d14-4031-af74-51aef94688a7 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=dacd1553-0852-4212-b1d1-a4e2d3e38648 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0


mount

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/EVOLUSHUN type fuseblk (ro,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by evolushun on 2007-10-22
Does that help any?

---

### Post by logos34 on 2007-10-22
For some strange reason ntfs-config did not add an entry for sda1 to fstab when it generated it.

try editing fstab:

**gksudo gedit /etc/fstab**

add this line:

> /dev/sda1 /media/EVOLUSHUN ntfs-3g defaults 0 0

Hopefully it will then automount rw.  Reboot.

info:
[http://www.ntfs-3g.org/index.html#usage](http://www.ntfs-3g.org/index.html#usage)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by evolushun on 2007-10-22
Well, I did that and now it doesn't even show my external or show it under Places>Computer.  What now?

---

### Post by logos34 on 2007-10-22
Some people have the hardest time with ntfs-3g...i don't know what it is.

check this:

system>admin>users&groups>manage groups>fuse>your username should be checked (as well as root)
[B]
gksudo gedit /etc/modules[/B]

if necessary add 

**fuse**

If nothing works after a couple of reboots then try adding the UUID for sda1 to fstab entry:

**blkid /dev/sda1**

---

### Post by evolushun on 2007-10-22
So, i removed that line and it wouldn't mount.  I then changed the properties of mount options to "ro" and it allows me to view the drive again.  I'm totally confused.

---

### Post by evolushun on 2007-10-22
OK...I did all that and will reboot now.

---

### Post by evolushun on 2007-10-22
Nothing...now what?

---

### Post by evolushun on 2007-10-22
I just saw you mentioned a UUID...how do I do that?

---

### Post by logos34 on 2007-10-22
It may be that there are some filesystem errors that are preventing ntfs-3g from working correctly or a problem with the program itself (either the config gui and/or ntfs-3g).

Follow [these instructions]("http://flomertens.free.fr/ntfs-config/participate.html") to run a bug report if you want.  Then backup and reformat as vfat or ext3

---

### Post by logos34 on 2007-10-22
> **evolushun said:**
> I just saw you mentioned a UUID...how do I do that?

copy the uuid to the beginning of the fstab entry just like the others.

---

### Post by evolushun on 2007-10-22
> **logos34 said:**
> copy the uuid to the beginning of the fstab entry just like the others.

I have no idea what that means.

---

### Post by logos34 on 2007-10-22
Just like in post #20, except change the sda1 to look like this:

> # Entry for /dev/sda1 :
UUID=<paste # here> /media/EVOLUSHUN ntfs-3g defaults 0 0

---

### Post by zeronothing on 2007-10-22
hello,

I know your pain, I just recently upgraded to gutsy and had problems mounting my ntfs external HDD. What I did to fix the problem was to uninstall "ntfs-3g" and "ntfs-config" using synaptic. Then I went to ntfs-3g website downloaded the newest source, compiled, and installed it. now I have no problems mounting my external ntfs HDD. I would like to mention that the latest stable release of ntfs-3g was not included with gutsy. By installing it this way you have the latest ntfs-3g installed. The readme included with the source is pretty simple to understand but that is me. if you need help don't hesitate to ask...

---

### Post by evolushun on 2007-10-22
I have fixed my problem.  I went ahead and did a clean install of 7.10.  I still had a problem so I went to my neighbors, hooked up my external and properly removed it, brought it home, plugged it in and it worked beautifully!  Something so simple!

---

### Post by Maestro23 on 2007-10-22
> **evolushun said:**
> I have fixed my problem.  I went ahead and did a clean install of 7.10.  I still had a problem so I went to my neighbors, hooked up my external and properly removed it, brought it home, plugged it in and it worked beautifully!  Something so simple!

Good deal.  Please mark this thread SOLVED using the Thread Tools.

Thanks.:)

---

### Post by logos34 on 2007-10-22
> **evolushun said:**
>  I still had a problem so I went to my neighbors, hooked up my external and properly removed it, brought it home, plugged it in and it worked beautifully!  Something so simple!

So that was it!  You hadn't safely removed/unmounted it the last time you were in windows (how long has it been anyway?).  I would've have thought in that case it wouldn't mount at all in linux, even read-only.

---

### Post by evolushun on 2007-10-22
I just got rid of windows permanently yesterday.

---

