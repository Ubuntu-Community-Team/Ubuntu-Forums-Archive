---
title: "problems with xubuntu 6.10 on oldworld powerbook g3"
date: 2007-04-10
forum: Apple PPC Users
---

### Post by arimed on 2007-04-10
I'm trying to install xubuntu 6.10 on an oldworld powerbook g3.
The machine specs are:
powerpc 292MHz, 192MB RAM, 8GB Hard disk, and it's an oldworld machine.
I'm using mac os9.1.

I used the xubuntu 6.10 alternate cd, copied the vmlinux and initrd.gz to the bootX directory, and booted the installer.

the first stages go well - I made the following partitions:
hda1-8: mac partitions
hda9: hfs+ partition
hda10: ~30MB ext2 partition mounted as /boot
hda11: ~6.9GB ext3 partition mounted as /
hda12: ~380MB swap area

then I set the timezone, users,  etc.

now comes the problem: when the base system installation starts, the installer read the packages from the cd and try to extract them into the HD. when it tries to extract the first package, it gets an error - as I understood it's a bad sector on the HD - and re-mounts  hda11 as read-only file-system, so it's impossible to continue the installation.

as I understand - the problem is of the harddisk, but the mac os9.1 installation had no problem, so why does the xubuntu have?

I hope I understood well the situation, if someone encountered such a problem, or has an idea if it's solvable - I woul'd be very happy to know,

thanks for the help

---

### Post by john_spiral on 2007-04-10
try booting off the ubuntu live CD and running a **fsck** check on the offending partition via the terminal.

---

### Post by erothoff on 2007-04-10
Are you actually trying to dual boot the machine? I installed Xubuntu on a iMac G3 but I didn't try to dual boot it. I just deleted Mac's OS. (Yes, I had to manually do the partitions the first time. I think if first used either YellowDog or SUSE when I did that. (I now have Xubuntu on it.)
  My guess is that Xubuntu is trying to write on the wrong partition. My iMac is apart at the moment, (had wanted to do a Memory upgrade, and didn't finish with it yet.) but I don't remember having a separate /boot partition.  It could be that Xubuntu is trying to copy to that partition and is running out of space.
  Sorry that I am not that helpful other than to let you know that Xubuntu DOES work on the old iMacs.  If other's can't help, let me know, and I can put it back together and try to help more.
  Good Luck...

---

### Post by arimed on 2007-04-10
I tried booting of the ubuntu breezy live cd, and I can't boot because the live cd giving me error: "The failing step is: Enter preinstalled session"
what can I do?

---

### Post by arimed on 2007-04-10
in oldworld macs, such as mine, it's impossible to boot without mac os installed. so I must have a small (~300MB) hfs+ partition with os9.1, and FROM THAT PARTITION boot the linux, using bootloader, like bootX.

thanks anyway.

---

### Post by lcafiero on 2007-04-13
Arimed --

The following page has some instructions for installing an earlier Ubuntu version on a PowerBook and these instructions may come in handy -- pay special attention to step 8.

[http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/](http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/)

I have been trying to get any *buntu on my PowerBook G3 Wallstreet with no success, although locally there is an installfest coming up on Saturday. I'd be interested to hear if you get Xubuntu up and running, and if you could post your efforts, I'd be grateful.

---

### Post by arimed on 2007-04-15
thanks for the advise.

I read the article, but my problem isn't listed there:
the partitioning step goes well, using the guided partitioning.
the problem is that right AFTER the partitioning, the filesystem partition is mounted as r/w filesystem.
BUT, when it starts to extract the installation packages using tar, from some reason, which I can't understand, that filesystem turns to be a read-only filesystem, and the installation fails.

I didn't manage to solve the problem yet, my guess is that it has to do with hardware problems - maybe the hard disk is damaged.

thanks anyway for the reply.
I'll post here if I find any solution.

---

### Post by mdknaebel on 2007-04-15
Are you using HFS Standard formatting?  I used OSX's partitioner from the boot disc, seemed to work for me.  When I tried HFS extended, It gave me an error....

---

### Post by arimed on 2007-04-15
as far as I understand, the error I get has nothing to do with the hfs filesystem, but with the new formatted ext3 filesystem. Do you think it matters if the mac partition is hfs or hfs+ ? I can't remember now if I tried both of these options, and the powerbook isn't in my reach now. If there is a difference between hfs and hfs+ please post here and I'll try to put my hand on the powerbook again and check it.

thanks

---

