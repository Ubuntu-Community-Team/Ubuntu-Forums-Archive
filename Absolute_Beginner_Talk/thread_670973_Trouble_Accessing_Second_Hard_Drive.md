---
title: "Trouble Accessing Second Hard Drive"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by btownray on 2008-01-18
Hi all, I just installed Ubuntu 7.10 last night, my first linux installation ever. I'm having trouble accessing my second SATA drive. (It's formatted to ntfs and was previously used as a storage drive for XP.)

 I was able to mount it and access it at first, but after trying to modify fstab to have it auto mount, it simply disappeared. Even after I reverted to my backup of fstab I can't find my second drive (sdb1) in the /dev folder.

One weird thing... usually my second drive isn't listed on the black and white screen when I boot up, but when I switch its cables with those of my primary drive, which is also SATA, they're both listed. (the booting doesn't continue, even after I changed the primary boot device in bios.)

I also tried booting in from CD and still wasn't able to find sdb1.

Any ideas?

---

### Post by rowanparker on 2008-01-18
Can you run ```
fdisk -l
``` as root please?

---

### Post by btownray on 2008-01-18
it still doesn't show up: 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4313    34644141   83  Linux
/dev/sda2            4314        4500     1502077+   5  Extended
/dev/sda5            4314        4500     1502046   82  Linux swap / Solaris

---

### Post by btownray on 2008-01-18
I saved a log from when it did actually work... here's what fdisk used to display:

```
ray@btown:~$ sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbeccbec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4313    34644141   83  Linux
/dev/sda2            4314        4500     1502077+   5  Extended
/dev/sda5            4314        4500     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe17a3a4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

```

---

### Post by Cresho on 2008-01-18
So I take it you can boot into windows and ubuntu.  You are dual booting fine?

---

### Post by btownray on 2008-01-18
I'm not dual booting... I formatted over my XP installation on my first hard drive and am using it to boot Ubuntu now.

---

### Post by hyper_ch on 2008-01-18
well, sdb1 is still a ntfs partition which is not a linux file system. Is there data on it that you need/want to access?

You can mount sdb1 as read-only quite easily or you could ust ntfs-3g to mount it as read/write.

---

### Post by btownray on 2008-01-18
Yeah it has some files that I absolutely need.. and my plan is to burn them onto a DVD and then maybe reformat the drive. but the problem is sdb1 isn't showing up at all anymore :confused:

---

### Post by hyper_ch on 2008-01-18
To mount it as read-only do this:

(1) create a mount point
```

sudo mkdir /media/ntfs

```
or
```

sudo mkdir /media/sdb1

```

(2) mount it:
```

sudo mount -t ntfs -ro /dev/sdb1 /media/ntfs

```
or
```

sudo mount -t ntfs -ro /dev/sdb1 /media/sdb1

```

Now it's mounted and accessible with read-only.

---

### Post by btownray on 2008-01-18
That's what I did to mount it, and it USED to work, but after rebooting my system it doesn't anymore. I ran the "ls" command in /dev and sdb1 isn't there anymore. I also can't see the hard drive in the "hardware information" section.

The only time my computer appears to see my second hard drive is when I switch its SATA cable with the one of my first hard drive. Booting up it shows them both, with my main hard drive as HDD 1... but it doesn't continue to Ubuntu and all I get is the "insert system disk and press enter" prompt.

I just tried reinstalling Ubuntu, fearing that I had accidentally messed up some system files while trying to get it to autoboot, but that hasn't fixed it.

---

### Post by hyper_ch on 2008-01-18
Hmmm, can you set in your bios that it should boot from the other drive? I can do that in mine (I mean set the boot order for each harddisk). That way you could change the drives so that it work but still boot from your current sda1.... you probably will need then to alter the grub entries...

---

