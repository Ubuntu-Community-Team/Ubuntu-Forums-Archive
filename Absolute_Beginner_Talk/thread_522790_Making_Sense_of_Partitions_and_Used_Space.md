---
title: "Making Sense of Partitions and Used Space"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ratioswitch on 2007-08-11
I hosed a bunch of settings on my new Dell Inspiron E1505n (running Ubuntu Feisty Fawn 7.0.4 with an 80 gig drive) while trying to install Ruby on Rails. Since it came direct from Dell with Ubuntu installed and a Ubuntu OS disc I decided to clean off the hard drive and re-install Ubuntu. I though everything went well and I went back using my new Ubuntu laptop. With that 80 gig drive I thought I'd have plenty of room for my needs but last week Ubuntu was nice enough to tell me that my HD was full. Using all of it's 10.5 GB of storage space. Whaaa!??!

I ran GParted and this is what it showed me:
[IMG]http://ratioswitch.com/files/dev-sda_GParted.jpg[/IMG]

As you can see, I'm working from /dev/sda7, which is an extended part of /dev/sda4. I would really like to have the space taken up by /dev/sda5, sda6, and sda8 ... as well as sda2 and sda3.

I DO know that /dev/sda1 holds the crap for Dell's special MediaDirect button that flanks my Dell's power button so I guess I'll have to leave that (The only this that button does, from what I can tell, is open my music player). Though I don't know why it's 54 meg.

Can someone out there help me better understand this file system, and more importantly, help me remove all these extra partions. I have heard of LVM ([http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)) and would like to know if this is an option for me since I want to do a clean install.

Also, every since I saw this screen from GParted I realized that I never received a back-up copy of any of the special drivers needed to run Ubuntu on this Dell. I figured I might as well figure all this out before I attempt a clean install again:) so I jumped on the Dell.com site and entered my Service tag number only to be presented with 4 driver files for my laptop ALL AS .EXE files! How do I use those on Linux?

Thanks for any help you can provide,
_rs

---

### Post by ratioswitch on 2007-08-11
Based on [one of the other related posts]("http://ubuntuforums.org/showthread.php?t=521626") in this forum ... here is my output for:

[B]sudo fdisk -l
df -h
cat /etc/fstab[/B]

- - - - - -

**sudo fdisk -l:**
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         269     2104515    6  FAT16
/dev/sda3             270         294      200812+  83  Linux
/dev/sda4             295        9729    75786637+   f  W95 Ext'd (LBA)
/dev/sda5             295         456     1301233+  82  Linux swap / Solaris
/dev/sda6             457        8274    62798053+  83  Linux
/dev/sda7   *        8275        9661    11141046   83  Linux
/dev/sda8            9662        9729      546178+  82  Linux swap / Solaris


**df -h:**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              11G  7.2G  2.8G  72% /
varrun                506M  280K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  128K  506M   1% /proc/bus/usb
udev                  506M  128K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2             2.1G     0  2.1G   0% /media/disk
/dev/sda1              55M  876K   54M   2% /media/DellUtility
/dev/sda3             193M  4.1M  180M   3% /media/os_part


**cat /etc/fstab:**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ac4d8b5d-063d-4be0-8150-13d7f4beabe0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=67cecc49-e1cf-41b4-80df-2ec62ad25936 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

- - - - -

Now I know installing RoR did not do all of this to my hard drive, I DID THIS while experimenting ... so I just would like help in fixing it :)

I would, at some point down the road, like to install and dual-boot this laptop with Fedora 7. I guess I would need to leave room for it when I re-partition everything.

Again, thanks!

---

### Post by ratioswitch on 2007-08-13
Well I found out from a different forum ([http://tinyurl.com/yw2aeb](http://tinyurl.com/yw2aeb)) that all I needed to do is create a LiveCD of GParted and run that in order to get rid of the extra/abandoned partitions and clean things up.

_rs

---

