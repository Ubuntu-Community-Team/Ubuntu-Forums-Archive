---
title: "Edgy installer not seeing partitions on powerbook g4"
date: 2006-11-09
forum: Apple PPC Users
---

### Post by rph on 2006-11-09
Hi all,

I'm trying to get a dual-boot Ubuntu/OS X setup going on my PowerBook G4--using the alternate 6.10 ppc installer cd.

I repartitioned the drive with Disk Utility so that I basically have: 1) a "placeholder" HFS+ partition that I want to erase and use to install Ubuntu (/dev/hda3, below); and 2) a journaled, case sensitive HFS+ partition that I've already used to install OS X (/dev/hda5, below).  But, for some reason, the Edgy installer wants to erase the entire drive.  I'm not sure why.

Anyway, when I drop into a shell from the installer cd, mac-fdisk sees the partitions:

```

/dev/hda1  Apple_partition_map  Apple  63 @ 1  ( 31.5k)  Partition map
/dev/hda2  Apple_Free    262144 @ 64  (128.0M)  Free space
/dev/hda3  Apple_HFS  Apple_HFS_Untitled_1  15466496 @ 262208     (  7.4G)  HFS
/dev/hda4  Apple_Boot  eXternal booter  262144 @ 15728704  (128.0M)  Unknown
/dev/hda5  Apple_HFSX  Apple_HFSX_Untitled_2  62149296 @ 15990848  ( 29.6G)  Unknown
/dev/hda6  Apple_Free    16 @ 781401444   (  8.0k)   Free space

```

What's the best thing to do here?

Rob

---

### Post by rph on 2006-11-10
hmm.  This seems to have been a problem for some time now.

[http://ubuntuforums.org/showthread.php?t=30749]("http://ubuntuforums.org/showthread.php?t=30749")

---

### Post by rph on 2006-11-13
Just thought I'd leave a note in case anyone else comes across this problem.  

The partitioning tool for the Edgy installer detects case *insensitive* HFS partitions just fine.  However, it cannot see case sensitive HFS partitions.

It would be nice if this was mentioned in the installation guide.

---

