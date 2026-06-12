---
title: "checkfs error during boot"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by kavoura on 2008-02-28
When booting Ubuntu, it recently keeps stopping part way through (but not every time) giving the following error:

fsck.ext3: No such file or directory while trying to open /dev/sde1

/dev/sde1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sde6

/dev/sde6: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

XANDROS: clean, 196455/3194880 files, 3324566/6367756 blocks
/dev/sdc5: clean, 13642/7077888 files, 13110033/14139200 blocks
/dev/sdd5: clean, 260/3843968 files, 2534950/3841535 blocks
/dev/sdd6: clean, 2255/2560864 files, 2215524/2560351 blocks
/dev/sda8: clean, 88484/3221344 files, 709065/6434024 blocks
/dev/sda9: clean, 347458/3106880 files, 2567660/6213130 blocks
/: clean, 672731/2305632 files, 3259460/4606630 blocks
/dev/sda10: clean, 27010/17334272 files, 23245828/34660229 blocks
fsck died with exit status 8


sde is a 400 GB hard drive attached via USB in an external casing.
There are 3 partitions, sde1 and sde6 are both formatted as ext3. sde5 is a swap partition.


Here are the entries for sde1 and sde6 in fstab:

/dev/sde1       /media/large2     ext3    defaults        0       2
/dev/sde6       /media/videos     ext3    defaults        0       2


Note that neither are referenced here by UUID, although a few of the partitions that are mounted are.

I have 5 hard drives in all, and only the USB 2.0 drive throws up this error. It is a new drive (actually a factory refurbished drive to replace a faulty drive, from Seagate). It does not always produce this error.

I have had no errors or problems with using the drive in normal operation in Ubuntu and there is no indication of other errors. The partitions were created using the Partition Editor in Ubuntu.

I am using Ubuntu 7.10, kept up to date with all updates. Using Gnome desktop. 
PC specs: AMD Athlon 2600 CPU, 1.5 GB RAM, all hard drives are IDE. Also have CD-RW and DVD-RW. 


What do the fsck errors mean and is there likely to be a problem with the USB drive? It has ext3 partitions but the fsck seems to think they are ext2.

---

### Post by Diabolis on 2008-02-29
Theres is nothing wrong with your system or your partitions. I'm guessing that the "error" appears only when the usb is unpluged.

When you boot your pc, linux will go over your fstab file to see which partitions should be mounted and where to place them. So if you boot your pc when the usb is unpluged, the "error" will tell you that the devices listed in the fstab file were not found.

If you get the error when the usb is pluged in, then you do have a problem and basically what it says is that the partition its corrupted.

---

### Post by kavoura on 2008-02-29
The USB drive is plugged in during boot up. So you are saying that the partitions are corrupt? but they work okay in Ubuntu. I am wondering why the file check seems to think they should be ext2 partitions when they are ext3.
How do I do a proper file system check on the partitions from within Ubuntu?

---

### Post by Diabolis on 2008-02-29
From my experience I know that partitions can give this error, but they'll still work. What I would do is to run a file system check on the hard drive that is giving you problems. The command is:
```
fsck
```
It is DANGEROUS to run it if the partition is mounted, run it only on unmounted disks. You can read more about it in the man page. Its similar to what happens to a windows pc when it is shutdown abruptly, like when the light goes off and you turn on the pc, you see a blue screen that says file system recovery. I think that'll fix it.

You can run fsck right after you get the error, while booting. It will ask you some things also, I wasn't sure about some stuff so I typed "yes" to all the questions and it worked. fsck also has a option that will asume "yes" so you don't have to type it in for every question, I don't remember which is the option but you can find it by typing:
```
fsck -h
```

---

### Post by kavoura on 2008-02-29
From within ubuntu, I unmounted both sde1 and sde6 and ran the fsck on them, these are the results:

root@ubuntu-pc3:/home/avoura# fsck.ext3 /dev/sde1
e2fsck 1.40.2 (12-Jul-2007)
/dev/sde1: clean, 199766/23445504 files, 27423188/46885694 blocks
root@ubuntu-pc3:/home/avoura# fsck.ext3 /dev/sde6
e2fsck 1.40.2 (12-Jul-2007)
/dev/sde6: clean, 1816/25149440 files, 21903236/50267377 blocks


Both partitions are regarded as being clean. I shall have to wait and see if there is an error next time the PC is booting, but it appears that both are free from errors.

---

### Post by kavoura on 2008-03-01
When I booted the PC today, it still gave me the error and stopped during boot. I ran fsck.ext3 on all my ext3 partitions (except root) and it reported them all as being clean.
The next step then maybe is to eliminate file system checking for the USB drive (sde) and see if that helps.

---

### Post by Diabolis on 2008-03-01
Since your systems thinks that your partitions are ext2, try checking the file system as a ext2 partition and see which is the output.
```
e2fsck
```

I think that it is better to run fsck and e2fsck while booting, right after the error has been shown.

What I would try next is to change their fstab entries, replacing their directory with the uuid. You can see which is their uuid by typing the following command in the terminal:
```
blkid
```

---

