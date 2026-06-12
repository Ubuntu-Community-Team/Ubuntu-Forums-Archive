---
title: "need help finding  the shared partition with windows xp?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-10-25
Gee... I feel so stupid..
I forgot where to find the shared (fat32) partition I created when installing ubuntu (dual-boot with XP). I can only see 'sda1' in /media folder and that is windows directory.
Thanks

---

### Post by bodhi.zazen on 2007-10-25
Open a terminal and enter :

```
sudo fdisk -l
```

For basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

For mounting windows partitions : [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Shazaam on 2007-10-25
nm, I'm too slow lol

---

### Post by phidia on 2007-10-25
Also try opening "Computer" from the top panel what shows up there?

---

### Post by genbuntu on 2007-10-25
oh, so I will have to mount it first , I guess..

Here's what comes up with fdisk -l :

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7088    56934328+   7  HPFS/NTFS
/dev/sda2            7089       10436    26892810   83  Linux
/dev/sda3           10437       11725    10353892+   b  W95 FAT32
/dev/sda4           11726       12137     3309390   82  Linux swap / Solaris


Places-> Computer only shows 3 things:  dvd drive; windows partition and filesystem

Thanks

---

### Post by bodhi.zazen on 2007-10-25
Your windows shared partition appears to be /dev/sda3

It is likely "windows partition" in "places"

you can confirm this with :```
mount
```

See the link I gave you for how to manage mounting and permissions.

---

### Post by genbuntu on 2007-10-25
ahh...  found it .. lol.. so simple . It was in 'filesystem' > 'windows' directory (I forgot that name). So can I rename the 'windows' folder to something else (like 'shared') safely from within ubuntu? It wouldn't mess up the files in it, would it?

I can see another 'fat32' directory in my 'filesystem' (/) , its empty. I wonder what that is for?

thanks bodhi.. I like the partitioning basics article you wrote (I'll go thru it in detail later).

EDIT: heres how I got to know : when I tried to mount  it gave the foll. error :
mount /dev/sda3
mount: according to mtab, /dev/sda3 is already mounted on /windows
mount failed

---

### Post by phidia on 2007-10-26
In linux/unix you need to mount a device to a mountpoint.

So for /dev/sd3 normally you would have a mount point in /mnt

you can issue this command > sudo mkdir /mnt/shared use any name you want in place of shared.

Then to mount do > sudo mount /dev/sd3 /mnt/shared

---

