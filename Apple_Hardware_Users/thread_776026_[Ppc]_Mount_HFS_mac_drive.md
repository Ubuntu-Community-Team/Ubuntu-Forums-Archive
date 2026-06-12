---
title: "[Ppc] Mount HFS mac drive ???"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by dennymoose on 2008-04-30
Anyone know if it is possible to mount and copy files from my HFS SCSI drive in Ubuntu 6.06 ??
It appears in the File Browser window, but says can't mount.

---

### Post by mrsteveman1 on 2008-04-30
There might not be an HFS+ driver in 6.06, its the 2.6.15 kernel i think, and it might predate the stable HFS+ driver everyone uses for this sort of thing, which was probably added or improved later on.

---

### Post by stream303 on 2008-04-30
Man, I hate to just point to a link in the ppc archives, but in order to save time, this might be the ticket:

[http://ubuntuforums.org/showthread.php?t=314743](http://ubuntuforums.org/showthread.php?t=314743)

Thanks Dirk and all involved with HFS recognition.  I know this is something that many want to do!

Caveat - I have never done this myself, and rest assured that me just pointing to a link isn't done with an "rtfm" attitude...

---

### Post by dennymoose on 2008-05-01
Well guess what. I'm so new to Linux, I don't have a clue how to even attempt to follow those instructions.
First off, I was under the impression that 6.06 was as new a release as I could use on b/w G3. I thought that was what it said on the download instructions. My updates did include 2.6.15-26 kernel. I figured out how to input command in terminal just now, but it brought back no info on my scsi drives, just the ata u-boot drive. They do appear in the device manager and in the file manager but don't work. (they are HFS not HFSplus)(seagate ultra scsi3 narrow) if that matters. when I try to mount in the file browser it says- error: device /dev/sdb3 (or sdc5) is not removable could not execute pmount-  don't got a clue

---

### Post by stream303 on 2008-05-01
> **dennymoose said:**
> Well guess what. I'm so new to Linux, I don't have a clue how to even attempt to follow those instructions.
First off, I was under the impression that 6.06 was as new a release as I could use on b/w G3. I thought that was what it said on the download instructions.

Ok, maybe it would be best to take it slow, and just work on getting a basic installation up and running first before tackling HFS issues.

The official download pages only mention what is "officially" supported, but there are many community-supported versions you can choose from.  For a first-time install, many would suggest the Feisty 7.04 "alternate" non-live install.  However, if you feel up to it, you could go with the latest Hardy 8.04, and again I'd recommend the "alternate" installer, but it's up to you.  See the following for these more recent releases:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Sinc you are running a G3, definitely refer to this article for some things you may have to do to get it running, especially the part about blank screens:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by slacka-vt on 2008-05-02
Just use the "Synaptic Package Manager" in System > Administration.
Perform a search for "hfsplus" and install the package(s).
You should now be able to mount your HFS disk by choosing it from your "Places" tab.

~s

---

