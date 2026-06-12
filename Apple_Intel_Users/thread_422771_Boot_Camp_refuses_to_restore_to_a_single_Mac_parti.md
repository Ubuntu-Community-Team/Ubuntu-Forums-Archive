---
title: "Boot Camp refuses to restore to a single Mac partition"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by SergioA on 2007-04-25
Hi there!

Following the great instructions at [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) I've succeded in installing Ubuntu 7.04 on my MacBook; now I'd like to revert to a single Mac os partition, so I thought that Boot Camp assistant could help in restoring the original configuration, but I've got the following message:

<<
The startup Disk cannot be partitioned or restored to a single partition.
The startup disk must be formatted as a single Mac OS Extended (journaled) volume or already partitioned by Boot Camp Assistant for installing Windows
>>

I think Boot Camp refuses to proceed because it sees the ext3 partition plus the swap one instead of the single partition for Window$ it originally created...

Any suggestion on how to proceed?

Thanks in advance and Ciao from Italy!

Sergio

---

### Post by Quicktime on 2007-04-25
you should be able to use your boot disk to help with this. restart your computer and boot from  your disk.  then instead of installing go the menus at the top of the screen and in one of them you should find the application disk utility.  this program should allow you to remove the partition. boot camp software does not work because it does not see the partition you made as xp. the boot disk should work best.

---

### Post by ronocdh on 2007-04-25
I concur with the QuickTime (haven't said that lately), but another option might be to run your Ubuntu live CD and just delete the Ubuntu partition. I agree that it's the ext3 formatting that's keeping OS X from trashing it; damn polite operating system!

---

### Post by SergioA on 2007-04-25
Ok, I succeded in deleting the partitions where I installed Ubuntu, so now I have 5 gb of free space.

So I thought of launching again Boot Camp to make it resize the Mac os partition to its original full size; but the only option it gives me is to partition again the hard disk to make room for Windows; and if I let it do so I get the following error:

<<
The disk cannot be partitioned because some files cannot be moved

Back up the disk and use Disk Utility to format it as a single Mac OS Extended (Journaled) volume. Restore your information to the disk and try using Boot Camp Assistant again.
>>

Any idea on how to recover those 5 gb "lost in space", without reformatting the HD and having to reinstall everithing from scratch?

Thanks for the patience & Ciao!!!

Sergio

---

### Post by ronocdh on 2007-04-25
> **SergioA said:**
> Ok, I succeded in deleting the partitions where I installed Ubuntu, so now I have 5 gb of free space.

So I thought of launching again Boot Camp to make it resize the Mac os partition to its original full size; but the only option it gives me is to partition again the hard disk to make room for Windows; and if I let it do so I get the following error:

<<
The disk cannot be partitioned because some files cannot be moved

Back up the disk and use Disk Utility to format it as a single Mac OS Extended (Journaled) volume. Restore your information to the disk and try using Boot Camp Assistant again.
>>

Any idea on how to recover those 5 gb "lost in space", without reformatting the HD and having to reinstall everithing from scratch?

Thanks for the patience & Ciao!!!

Sergio
One more idea: try formatting the old Ubuntu partition as FAT32. I'm in OS X right now, and when I open Disk Utility I am given the option to "Erase free space" on my WinXP party, which is FAT32, but **not** on my Ubuntu party, which is ext3. You could use DU to format, or the Ubuntu Live CD again.

Alternatively, maybe [GParted]("http://gparted.sf.net") would nuke it for you. Or you could use it just to format to FAT32, then erase in DU, etc. Post back!

---

### Post by Enderend on 2007-05-01
I had the same problem.  Here was how I had to fix it:

Back up your Mac.  I use rsync and an external drive.  [Here's a great tutorial]("http://www.egg-tech.com/mac_backup/").  

Boot from your OS X install DVD.  Format your drive completely.  Reinstall OS X.  If you backed up to an external HD, use the migration tool to restore your Mac.

---

### Post by ronocdh on 2007-05-01
> **Enderend said:**
> I had the same problem.  Here was how I had to fix it:

Back up your Mac.  I use rsync and an external drive.  [Here's a great tutorial]("http://www.egg-tech.com/mac_backup/").  

Boot from your OS X install DVD.  Format your drive completely.  Reinstall OS X.  If you backed up to an external HD, use the migration tool to restore your Mac.
This is great to know and I hope very much that it solves SergioA's problem; however, I think it would be very nice if someone found a method that didn't take all this work! Has no one found a way? Everyone resorts to this tactic? (I know I myself when I was still juggling sizes.)

---

### Post by SergioA on 2007-05-01
Hi guys!

Many thanks for your help, I succeeded in restoring to the original single Mac OSX partition in two steps:

- by using Gnome Partition Editor live CD I deleted the two Linux partition (but then GPE has some trouble resizing the Mac OSX partition)

- so I used iPartition (a program specifically made for Macs) from a bootable CD and restored the Mac OSX partition to its full size

Ciao for now!

Sergio

---

