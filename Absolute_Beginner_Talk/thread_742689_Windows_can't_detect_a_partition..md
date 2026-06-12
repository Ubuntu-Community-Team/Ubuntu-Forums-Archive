---
title: "Windows can't detect a partition."
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by sy88 on 2008-04-01
Hi all, this is my first time posting on these forums.

That aside, I have recently installed Ubuntu Gutsy Gibbon 7.10.  Everything was working out fine, but now my Windows ( C: ) partition is sees my D: as RAW, but can still see the E: drive.

Currently, my setup is 2 500 GB HDD's.  1st one has C: (Vista) and E: (data).  2nd one has (had) D: (data 2) and my Linux partition.  Ubuntu can see my D: drive but Windows cannot.

Could anyone help me out? Thanks.

---

### Post by Tatty on 2008-04-01
can you post the output from ```
sudo fdisk -l
```

---

### Post by sy88 on 2008-04-01
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b1d6226

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sda2           12749       60802   385984512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc754c754

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       55455   445440000    7  HPFS/NTFS
/dev/sdb2   *       55456       60576    41134432+  83  Linux
/dev/sdb3           60577       60801     1807312+   5  Extended
/dev/sdb5           60577       60801     1807281   82  Linux swap / Solaris

```

/dev/sdb1 is my D: which I'm unable to access.

---

### Post by aroustaei on 2008-04-01
Hi
Use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to fix your partition.
very powerful l:)

---

### Post by sy88 on 2008-04-02
> **aroustaei said:**
> Hi
Use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to fix your partition.
very powerful l:)

I'm sorry, could you perhaps guide me through what I have to do?  I've fiddled a bit but am unable to obtain any results.

---

### Post by mrsteveman1 on 2008-04-02
I don't see any problems with the partition structure, the partition ID 7 is correct, and Windows apparently has a drive letter still assigned but sees the partition as raw, so NTFS is probably corrupt for some reason.

Run chkdsk on the drive in windows by opening a command prompt and typing:

```
chkdsk d:
```

Then you can see if chkdsk found errors.

If chkdsk found errors you can either run the program again with the /f switch to fix them:

```

chkdsk /f e:
```

Or you can use testdisk which should be able to fix the partition, but try the windows tools first.

---

### Post by sy88 on 2008-04-02
> **mrsteveman1 said:**
> I don't see any problems with the partition structure, the partition ID 7 is correct, and Windows apparently has a drive letter still assigned but sees the partition as raw, so NTFS is probably corrupt for some reason.

Run chkdsk on the drive in windows by opening a command prompt and typing:

```
chkdsk d:
```

Then you can see if chkdsk found errors.

If chkdsk found errors you can either run the program again with the /f switch to fix them:

```

chkdsk /f e:
```

Or you can use testdisk which should be able to fix the partition, but try the windows tools first.

I ran chkdsk D: once already and it didn't return any errors.  I'm currently retrying with /f and /r.

---

### Post by sy88 on 2008-04-02
Those didn't help.  chkdsk recognizes my D drive as a legitimate NTFS partition and finishes with no errors.    However, Windows still doesn't see it.

---

### Post by aroustaei on 2008-04-02
download this version of testdisk for windows
[http://www.cgsecurity.org/testdisk-6.9.win.zip]("http://www.cgsecurity.org/testdisk-6.9.win.zip")
here
in zip file there is documentation. there is recovery examples see this
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples")
hope be usefull

---

### Post by sy88 on 2008-04-02
I tried using testdisk, aroustaei, and it can see my D: and says the boot sector is ok.  However upon choosing the option 'Repair MFT' for my D: it says "Both MFT seems ok but they don't match, use chkdsk".

That makes me go in a full circle since chkdsk said there were no problems...:(

---

### Post by Zralou on 2008-04-02
You don't have the partition set as 'hidden' by any chance?, I know unlikely, but worth a look ("show all files" in folder options).

Sara Lou

---

### Post by sy88 on 2008-04-02
No, Windows SEES the drive but upon double-clicking...says it's inaccessible and corrupted/unreadable.

---

### Post by mrsteveman1 on 2008-04-02
I'm curious what the Linux tools think about this partition, have you tried mounting the partition with ntfs-3g?

---

### Post by sy88 on 2008-04-02
> **mrsteveman1 said:**
> I'm curious what the Linux tools think about this partition, have you tried mounting the partition with ntfs-3g?

No, I haven't tried ntfs-3g, but Ubuntu mounts/reads/writes to my D: perfectly.

---

### Post by mrsteveman1 on 2008-04-02
If this is an NTFS partition, and you are using gutsy, you are already using ntfs-3g since it uses it by default.

This in effect means the filesystem is fine, and perhaps something is weird with Windows ability to assign a drive letter to the partition. Windows refers to mounting filesystems as assigning a drive letter, so you can try going into the disk manager (control panel> admin tools> computer management > disks) and assign a different letter to that partition and see what happens.

---

### Post by sy88 on 2008-04-03
> **mrsteveman1 said:**
> If this is an NTFS partition, and you are using gutsy, you are already using ntfs-3g since it uses it by default.

This in effect means the filesystem is fine, and perhaps something is weird with Windows ability to assign a drive letter to the partition. Windows refers to mounting filesystems as assigning a drive letter, so you can try going into the disk manager (control panel> admin tools> computer management > disks) and assign a different letter to that partition and see what happens.

Thanks for notifying me about ntfs-3g.

I tried changing letter but still to no effect.  Windows still sees it as RAW and says it needs to be formatted.

---

### Post by sy88 on 2008-04-04
Does anyone have any other ideas?

---

### Post by mrsteveman1 on 2008-04-04
I'm stumped, if chkdsk said its ok,, ntfs-3g is mounting it (meaning the journal is clean, or it would refuse), but windows refuses to mount the filesystem....

What's telling i suppose is the testdisk result, saying the backup MFT doesn't match the first one, which is an obvious problem testdisk should be able to correct. 

I have no idea whats going on, but i'll play around with testdisk a bit, make some test partitions and see what happens.

---

