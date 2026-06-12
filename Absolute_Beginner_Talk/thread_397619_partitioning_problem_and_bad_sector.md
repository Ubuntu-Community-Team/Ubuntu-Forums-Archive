---
title: "partitioning problem and bad sector"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by hwheller on 2007-03-30
I have been trying to dual boot install Ubuntu without success.  I have a Dell Optiplex 170L running Windows XP.  1 GB memory, 80 GB hard drive.  I tried installing from Ubuntu 6.06 Live CD.  First I tried the automatic partitioning and it failed at partitioning.  I tried manual and it failed again.  I later went to the Desktop and used the Terminal to "sudo gparted" and it failed to partition.  In each case it sees the drive and shows the partitions.  At some point it says "failed to move or reduce..."  Just a few minutes ago I used qtparted on System Rescue CD.  It said that there is at least one bad sector on the drive and quit.  I haven't yet run the Window error checking tool, but will it be impossible to repartition if there is a bad sector?  Would it be best to replace the hard drive?

---

### Post by NyteGeek on 2007-03-30
> **hwheller said:**
> I have been trying to dual boot install Ubuntu without success.  I have a Dell Optiplex 170L running Windows XP.  1 GB memory, 80 GB hard drive.  I tried installing from Ubuntu 6.06 Live CD.  First I tried the automatic partitioning and it failed at partitioning.  I tried manual and it failed again.  I later went to the Desktop and used the Terminal to "sudo gparted" and it failed to partition.  In each case it sees the drive and shows the partitions.  At some point it says "failed to move or reduce..."  Just a few minutes ago I used qtparted on System Rescue CD.  It said that there is at least one bad sector on the drive and quit.  I haven't yet run the Window error checking tool, but will it be impossible to repartition if there is a bad sector?  Would it be best to replace the hard drive?

You should make sure that the windows partition is defragmented from windows, run chkdsk to make sure there are no file system errors, and make sure there is plenty of free space on the drive before trying to re-partition it. You might have to free up some space if it is failing on you or you might have file system errors.

---

### Post by mi_were on 2007-03-30
> **hwheller said:**
> I have been trying to dual boot install Ubuntu without success.  I have a Dell Optiplex 170L running Windows XP.  1 GB memory, 80 GB hard drive.  I tried installing from Ubuntu 6.06 Live CD.  First I tried the automatic partitioning and it failed at partitioning.  I tried manual and it failed again.  I later went to the Desktop and used the Terminal to "sudo gparted" and it failed to partition.  In each case it sees the drive and shows the partitions.  At some point it says "failed to move or reduce..."  Just a few minutes ago I used qtparted on System Rescue CD.  It said that there is at least one bad sector on the drive and quit.  I haven't yet run the Window error checking tool, but will it be impossible to repartition if there is a bad sector?  Would it be best to replace the hard drive?

you will eventually have to replace the hard disk, the sooner the better. It however presents the you with the perfect location for trying out new distros of linux or whatever catchs your fancy.

As a first step run scandisk or its equivalent in your current OS to see how bad the disk is. As a rule of thumb whenever I have had bad sectors appear on a drive it has been on its last legs.

Best of luck.

---

### Post by hwheller on 2007-03-31
Thanks for your suggestions.  I had defragmented four times this week with two different  programs.  There is about 22GB used of 76GB.  I had Windows check the disk last night.  It reports some bad sectors, but didn't fix them although I did check that option.  I tried both gparted and qtparted again this morning with the same results.  I guess I'll have to wait until I replace the hard drive to install Ubuntu.  Thanks for your help.

---

