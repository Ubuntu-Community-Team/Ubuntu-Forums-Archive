---
title: "dual boot question"
date: 2009-06-16
forum: Apple Hardware Users
---

### Post by babybatter23 on 2009-06-16
ok first off i have a MB aluminum 2.4ghz 2gb RAM running leopard

i want to dual boot ubuntu 9.04 without losing my data

basically the first problem that i hit was partitioning my HD when i go to disk utility and set up a partition trying to use the remaining 65 gb on my computer i make a 20gb partition named ubuntu however it wont let me choose free space as a format option and only allows the osx journaled format, thanks in advance

---

### Post by Rog-Mahal on 2009-06-16
The format doesn't matter. Once you boot your Ubuntu LiveCD, you can reformat that new partition to whatever format you like. [Here are the community docs for dual booting OS X and Ubuntu.]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu")

---

### Post by Richardcavell on 2009-06-16
Mate,

Don't do the partitioning in Disk Utility.  Or, for that matter, within OS X.  Boot to the Ubuntu Live CD.  (Burn the .iso file to a CD and then reboot, holding down the alt-option key).  The Ubuntu Live CD will know what to do.

Richard

---

### Post by cyberdork33 on 2009-06-16
> **Richardcavell said:**
> Mate,

Don't do the partitioning in Disk Utility.  Or, for that matter, within OS X.  Boot to the Ubuntu Live CD.  (Burn the .iso file to a CD and then reboot, holding down the alt-option key).  The Ubuntu Live CD will know what to do.
Honestly, for resizing your HFS+ partitions, Disk Utility is much more trusted.

Basically, just create a new partition on the disk, name it and format it whatever you like (it won't matter).

boot up the Ubuntu live cd and start gparted (AKA Partition Editor). Use gparted to delete the new partition you just created It will likely be partition #3 (this will leave free space). 

Then start the installer and choose to install to the largest free space as indicated in the community docs. Good Luck.

P.S. When identifying your mac, please use the version string as can be found here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Richardcavell on 2009-06-16
By the way,

I accept that Apple's Disk Utility is best for HFS+ work.  (GParted has a couple of bugs and cannot perform some operations, such as growing an HFS partition).

However, it's only the Leopard version of Disk Utility that can non-destructively resize a HFS+ partition.

If he doesn't have Leopard, he's going to have to use GParted.  And if you make backups (for Christ's sake do this), it doesn't matter if it stuffs up.

Richard

---

### Post by cyberdork33 on 2009-06-16
> **Richardcavell said:**
>  However, it's only the Leopard version of Disk Utility that can non-destructively resize a HFS+ partition.

> **babybatter23 said:**
> ok first off i have a MB aluminum 2.4ghz 2gb RAM **running leopard**
emphasis mine

> **Richardcavell said:**
>  And if you make backups (for Christ's sake do this), it doesn't matter if it stuffs up.yes, please do backup.

---

### Post by Richardcavell on 2009-06-17
Cyberdork,

You are correct to point that out.

I don't have Leopard.  I recently increased the size of my HFS+ partition.  The only way to do it was to back it up, delete the old partition, use GParted to delete the old partition and install a new, larger one, use gptsync.efi from refit to fix my MBR (which GParted doesn't fix properly), then copy my backup back onto the new partition.

It's painful, and slow, to do this, but I guess I have no other way... actually, could I set up my computer as a target disk via firewire and get another computer running Leopard to resize it?

Richard

---

### Post by cyberdork33 on 2009-06-17
> **Richardcavell said:**
>  It's painful, and slow, to do this, but I guess I have no other way... actually, could I set up my computer as a target disk via firewire and get another computer running Leopard to resize it?
Possibly. I dont really see a reason it wouldn't.

Also, the underlying tools that actually do the resizing are in Tiger, there is just no interface to use them in Disk Utility.
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

---

### Post by babybatter23 on 2009-06-19
thank you for all of your help and advice i loaded up my ubuntu live cd after using boot camp assistant to make the partition and than after installing linux downloaded REFIT to assist in dual booting and everything works great... im already considereing switching all the way to linux

---

