---
title: "Grub trouble after installing new linux headers"
date: 2012-11-02
forum: Any Other OS
---

### Post by ekoz on 2012-11-02
Hi,

I am a Ubuntu user, but here I have some difficulties with my debian and I'm trying to fixed it with my Ubuntu live key so if you can help me please...

I guess after installing a new linux kernel grub messed up. 
I tried (like many times before) to install grub again thanks to chroot and grub-install but this time it doesn't work.
I tried again to fixed it with boot-repair still on my ubuntu key but same consequences as previously (here is the report... [http://paste.ubuntu.com/1324347/](http://paste.ubuntu.com/1324347/))

I really don't know what to do...

It tells me : ```

could not stat the resume device file /dev/sda5

```
But I don't have any sda5 partition!

And the next error is :
```

mount: mounting /dev/disk/by-uuid/94100b[...] on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Trying passing init=bootarg.

```

If you have any idea to install my grub...

---

### Post by oldfred on 2012-11-02
Moved to Other OS since Debian and welcome to the forums.

I do not know Debian, but I cannot see anything out of place in your BootInfo report. Are you booting from sda? Even though you have grub in the other MBRs, it is usually better to boot from drive with install.

I have never compiled a kernel, but is the sda5 left from the system where you compiled it? 

Since you have two larger drives.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by ekoz on 2012-11-02
hello,

I'm sorry I know it's the Ubuntu forum, but because I saw topics on other forum relative to my problem and Ubuntu I've posted here...

Actually I found a solution :
[http://blog.dvl.pl/article/2009/10/02/resume-could-not-stat-the-resume-device-file/]("http://blog.dvl.pl/article/2009/10/02/resume-could-not-stat-the-resume-device-file/")

*sda5* was specified on this file, you are right I have changed partition but I haven't reboot since a long time...
So now I have to run **dpkg-reconfigure uswsusp** to save changes after have added *sda2*. But I cannot boot on my partition to run it :confused:

Do you know how to do? Cause I tried to chroot from a Ubuntu live key without success

I'm getting cray! :mad:

---

### Post by kiyop on 2012-11-03
[http://paste.ubuntu.com/1324347/](http://paste.ubuntu.com/1324347/)
> 
=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.

# <file system>                    <mount point>        <type>                <options>            <dump>  <pass>
proc                        /proc            proc                defaults            0    0
UUID=94100b57-abed-467e-bd22-e06c22d3bc6e    /            ext4                errors=remount-ro        0    1
UUID=231d417f-461f-4fb1-a25b-582effca0da6    none            swap                sw                0     0
#UUID=392dcdc7-832b-4035-a722-f50473614612    /home            ext4                defaults            0    0 
UUID=3ad4f68f-11f7-44cf-8aa4-a113be3e9fc6    /home            ext4

(snip)

/dev/sda1: UUID="94100b57-abed-467e-bd22-e06c22d3bc6e" TYPE="ext4"
/dev/sda2: UUID="231d417f-461f-4fb1-a25b-582effca0da6" TYPE="swap"
/dev/sdb1: UUID="3ad4f68f-11f7-44cf-8aa4-a113be3e9fc6" TYPE="ext4"
/dev/sdc1: UUID="392dcdc7-832b-4035-a722-f50473614612" TYPE="ext4"
You changed /home from /dev/sdc1 to /dev/sdb1, didn't you?
Did you copy all the contents in /dev/sdb1 to /dev/sdb1?

I don't watch often here; ubuntu forums.
If you want my quick reply, please post at debian forum: [http://forums.debian.net/](http://forums.debian.net/)
If you post at debian forum on this problem of yours, write so here.

Added at 2012/11/3 in Japan;

The OP sent me a private e-mail.
The OP posted at [http://forums.debian.net/viewtopic.php?f=10&t=87647](http://forums.debian.net/viewtopic.php?f=10&t=87647)

---

