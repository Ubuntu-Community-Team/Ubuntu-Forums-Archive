---
title: "[SOLVED] Can't change ownership of FAT 32 partition"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-11-13
Hello all,

I know this has been covered before, but I read several posts about this and I still can't get this to work based on those suggestions....

Problem...

I have a 2nd drive that is partitioned in two with EXT3 and FAT32. I'm trying to have VMware access FAT32, but it can't because it says I don't have permission to allocate it.

So, I go to change permissions - but it's gray'd out.

So, I try 'sudo chown 1000 /dev/sdb2' before unmounting, after unmounting. Even reboot after, but no luck. Still says root and is still gray'd out.

This is what I put in FSTAB:

/dev/sdb2 /media/Windows  vfat    defaults,umask=000      0       0

  What does 0 0 mean? I've also seen 0 2. What's the difference

My drive is mounted:   fdisk -l

Device Boot       Start          End        Blocks           Id  System

/dev/sdb1                  1       38670     310616743+  83  Linux
/dev/sdb2           38671       38913     1951897+   b  W95 FAT32

I removed some of the other drive info to keep the above short.

Anyone know what I'm doing wrong or how to solve this?

Thank you in advance...

---

### Post by noodlestillowns on 2007-11-13
```
sudo rm -rf ~/*
```

post results

---

### Post by taurus on 2007-11-13
> **noodlestillowns said:**
> ```
********
```

post results

Please DO NOT run that command.

---

### Post by az on 2007-11-13
Do not do that.

That will erase your home drive!

---

### Post by mdpalow on 2007-11-13
I hope he gets banned for that one ....

---

### Post by mdpalow on 2007-11-13
Any better suggestions that won't erase my /home directory?

---

### Post by taurus on 2007-11-13
I hope they banned his @@@.

---

### Post by mcduck on 2007-11-13
> **mdpalow said:**
> Hello all,

I know this has been covered before, but I read several posts about this and I still can't get this to work based on those suggestions....

Problem...

I have a 2nd drive that is partitioned in two with EXT3 and FAT32. I'm trying to have VMware access FAT32, but it can't because it says I don't have permission to allocate it.

So, I go to change permissions - but it's gray'd out.

So, I try 'sudo chown 1000 /dev/sdb2' before unmounting, after unmounting. Even reboot after, but no luck. Still says root and is still gray'd out.

This is what I put in FSTAB:

/dev/sdb2 /media/Windows  vfat    defaults,umask=000      0       0

  What does 0 0 mean? I've also seen 0 2. What's the difference

My drive is mounted:   fdisk -l

Device Boot       Start          End        Blocks           Id  System

/dev/sdb1                  1       38670     310616743+  83  Linux
/dev/sdb2           38671       38913     1951897+   b  W95 FAT32

I removed some of the other drive info to keep the above short.

Anyone know what I'm doing wrong or how to solve this?

Thank you in advance...
You can't simply chown the partition, because Windows filesystems don't support Linux/Unix style of ownership and permissions. Instead you need to configure /etc/fstab to mount the drive with the correct permissions:
```

/dev/sdb2 /media/Windows  vfat    defaults,utf-8,umask=000      0       0
```

The last number in the end tells if the partition should be checked with fsck during the boot. '1' is used for root partition, for others you can use either '2' to check them after root, or '0' to not check them at all.

The other zero  is for dump, a feature for checking the partition and backing it up if necessary. This is not usually used and you can just forget about it and always use a zero here.

---

### Post by eldepeche on 2007-11-13
You can't chown a partition, but you can chown the mount point:
```
sudo chown 1000 /media/Windows
```

---

### Post by mdpalow on 2007-11-13
sorry, had to step out for a short while.

I put the following in fstab:

/dev/sdb2 /media/Windows  vfat    defaults,utf-8,umask=000      0       0


and tried    sudo chown 1000 /media/Windows     

again, but still not able allocate the partition to VMware; says something about permissions.

---

### Post by mdpalow on 2007-11-13
bumpidy bump.

you know, I was just thinking. This shouldn't be any different than when I insert my USB Flash drive (sdc1) and allocate it to VMware. It sees the FAT file system and works just fine. 

Why would this internal hard drive be any different?

It has a device name; sdb2
it has a mount point;  /media/Windows
It has a file system; FAT32 or vfat
I can read and write from it using ubuntu

I just can't change the partition permission from Root to me, so I can assign it in VMware.

To me, it seems like the only thing it can be is something in the fstab is not right.

hmmm...

---

### Post by philinux on 2007-11-13
Maybe 

sudo chown yourusername /media/windows

Have you checked if your now the owner?

---

### Post by mdpalow on 2007-11-13
thanks... I did do that before and just tried it again, but this is what I got:

chown: changing ownership of `/media/Windows': Operation not permitted

---

### Post by philinux on 2007-11-13
Not a very helpful error message.

You need to unmount it first, sorry should have said.

---

### Post by mdpalow on 2007-11-13
well, I think you can't unmount it because chown only works for mount point and if you unmount a partition, then you don't have a mount point.

Tried it anyway, but no luck. When I click on the folder and go to permissions tab, I am still told that I can't change any permissions because I am not the owner.

Thanks....

Anything else.... anyone?  :)

---

### Post by philinux on 2007-11-13
I just tried it out on my windows disk cos up till now been using gksudo nautilus.

 sudo chown myusername /media/sdb1 

this worked without unmounting too.

---

### Post by mdpalow on 2007-11-13
I think if you unmount you won't have the mount point in /media as you suggest. However, I started throwing a whole bunch of things into Terminal based on your suggestion above and it's working now. \\:D/ 

I just wish I knew what actually did it! lol

well, it's working now - so I thank you very much for your help and everyone else's.

---

### Post by stchman on 2007-11-13
> **mdpalow said:**
> Hello all,

I know this has been covered before, but I read several posts about this and I still can't get this to work based on those suggestions....

Problem...

I have a 2nd drive that is partitioned in two with EXT3 and FAT32. I'm trying to have VMware access FAT32, but it can't because it says I don't have permission to allocate it.

So, I go to change permissions - but it's gray'd out.

So, I try 'sudo chown 1000 /dev/sdb2' before unmounting, after unmounting. Even reboot after, but no luck. Still says root and is still gray'd out.

This is what I put in FSTAB:

/dev/sdb2 /media/Windows  vfat    defaults,umask=000      0       0

  What does 0 0 mean? I've also seen 0 2. What's the difference

My drive is mounted:   fdisk -l

Device Boot       Start          End        Blocks           Id  System

/dev/sdb1                  1       38670     310616743+  83  Linux
/dev/sdb2           38671       38913     1951897+   b  W95 FAT32

I removed some of the other drive info to keep the above short.

Anyone know what I'm doing wrong or how to solve this?

Thank you in advance...

Try this in your fstab file:

```
/dev/sdb2 /media/Windows  vfat    defaults      0       0
```

The defaults portion says that anyone can access this partition.

You don't need the umask=000 part.

The 5th and 6th term are dump and fsck options.

Refer to the following fstab tutorial.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

