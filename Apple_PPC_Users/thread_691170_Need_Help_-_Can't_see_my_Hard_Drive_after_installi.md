---
title: "Need Help - Can't see my Hard Drive after installing Ubuntu"
date: 2008-02-08
forum: Apple PPC Users
---

### Post by noblenull on 2008-02-08
I attempted (unsuccessfully) to install Ubuntu on a G3 iMac. I had a lot of trouble getting it to boot successfully, so I now want to go back to OS X. However, when booting from the CD with an OS 9 or OS X disk, they cannot see the hard drive to reformat.

Can anyone point me in the right direction? I assume that there is some type of boot loader that taking control prior to the CD booting.

---

### Post by PapaNerd on 2008-03-19
I've no idea what might be taking control, but one approach to solving the problem would be to nuke the data on the drive.  A tool like disc-wipe (available at [http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe)) would certainly do that.

---

### Post by stream303 on 2008-03-19
I can't speak for OS9, but with an OSX boot disk, bring up disk utility.  Disk utility should find your drive and you can let it repartition it.  Once partitioned, the installer should have no problems.

Warning!  Have you *ever* had OSX installed on this machine?  If not, you need to do an openfirmware upgrade.  If you don't, there is the possibility that it can leave the machine in an unusable state.

---

### Post by ristosu on 2008-03-19
On OS 9 install CD there is a program named Drive Setup in Utitilies folder.

In any case, before installing OS X, the firmware should be updated. And that has to be done from within OS 9 that is installed on the hard disk. On a slot-loader the version should be 4.1.9f1.

---

