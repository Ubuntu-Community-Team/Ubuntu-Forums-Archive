---
title: "Triple Boot: Mac OS X, Karmic 9.10, Windows XP on MacBook 1.1"
date: 2009-10-31
forum: Apple Hardware Users
---

### Post by pizzacake on 2009-10-31
It's tricky to Triple Boot: Mac OS X, Karmic 9.10, Windows XP MacBook 1.1

thanks to lot's of XP bugs that can trip you up.  This is the method that worked for me on my MacBook 1.1. Props to [http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134)

I have a 320GB HDD partitioned as:
1. 200MB EFI Partition
2. 200GB HFS+ Partition

In order to install XP without the dreaded hal.dll error, you cannot have more than 4 partitions.  Also XP must be installed to partition 4 not 3.

Open disk utility and create two partitions after your OS X partition.  In my case

3. 90GB HFS+ Partition
4. 30GB FAT Partition

Note: Make partition 3 a format Windows XP doesn't understand otherwise it will throw important system files during installation on partition 3 despite the fact you're installing on partition 4!  You'll then have to transfer those important system files to partition 4 otherwise XP won't boot.  During Ubuntu installation you can change partition 3 format to EXT4.

Note: For XP don't make partition 4 any bigger than 30GB again due to an XP bug you'll get disk error messages with bigger partitions.

Now install XP to partition 4.  

Now install Ubuntu.  When it comes to choosing where to install Ubuntu choose manual partitioning.  Change partition 3 format to EXT4; mount point should be root /.  A swap space warning will appear but just ignore it and select continue.  I believe part of partition 3 can be set up to be used for swap space.  Finally, step 8 of 8 choose advanced options: device for boot loader - it's important you don't choose hda or whatever instead choose the EXT4 partition 3 i.e. /dev/sda3

Done!

Holding down the option key at boot only displays OS X and Windows partitions to boot from however using refit you can see all three.

---

