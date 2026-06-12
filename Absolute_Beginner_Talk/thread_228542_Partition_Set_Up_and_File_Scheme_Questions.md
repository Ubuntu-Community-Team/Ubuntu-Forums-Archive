---
title: "Partition Set Up and File Scheme Questions"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by lou1998 on 2006-08-03
Hi all,
I am somewhat of a newbie to Linux and have a couple questions.

I just built a new computer with 2x 160GB SATA drives.  I want to install Kubuntu and was wondering if there is a particular partitioning format to use.  ie /root 10GB /home 50GB etc. or should I just use one big 200GB / partition?

Also, I have 2GB of ram.  Is it necessary to have a /swap partition?

Finally, where is the standard place to install common files like apps, games, pictures, music etc so that other people can access them?  In windows I put them on the D: drive.  Is /home appropriate or somewhere like /usr/local/

Thanks for any help you give!

---

### Post by ewl1217 on 2006-08-03
The partitioning scheme is up to you. Many people use seperate home ( /home ) and root ( / ) partitions. This makes sure that you can do a clean install again later and keep all your personal settings. Personally, I just prefer one big root partitionso I dno't have to worry about running out of space on any of them. Some people also prefer having a seperate boot ( /boot ) partition.

With two gigs of ram, you probably don't need a swap partition. If you'll be doing anything **EXTREMELY** memory-intensive you might need it, but I highly doubt it.

As far as installing programs go, I reccomend installing everything via apt, through a program like Adept, apt-get or aptitude. This will make installations of programs easy and make sure that everyone can access prgrams. I think you're best not to install any programs manually, or from source, until you're more used to Linux or that's the only way to get them.

**EDIT:** I missed the part about sharing photos, music and other files. For those, you could just make a seperate directory (or partition) that everyone has read-only, or possibly read and write, access to.

---

### Post by rpaller on 2006-08-03
I would still define a /swap partition. When you have that much disk space are you really going to miss 1 or 2 GB?

You have a couple options regarding your shared files. You could create a partition for /usr and then place a folder under /usr/share. You could simply create a folder in /home and grant the necessary privileges for groups and/or users. Or even create a dedicated partition for them and then define the group and/or user permissions.

---

