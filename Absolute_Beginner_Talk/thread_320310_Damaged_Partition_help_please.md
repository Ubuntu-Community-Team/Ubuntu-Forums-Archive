---
title: "Damaged Partition help please"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by xxlbstripesxx on 2006-12-17
After a few days of searching i found out that in my first attempt to install any non-windows OS ever i damaged my partition. I tried to run testdisk using the following terminal command: 

sudo apt-get install testdisk

however that only gives me this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package testdisk

I was wondering if there is anyone who could help me figure out how to get testdisk to work or how to get my comouter in working condition in general so that I can use my Ubuntu, Windows, and My FAT32 partitions or even just get me back to straight Windows at last resort. Any help would be appreciated. Thank You.

---

### Post by gn2 on 2006-12-17
What do you mean by "damaged my partition" ?

What Operating System(s) are installed currently?

---

### Post by aysiu on 2006-12-17
[*testdisk* appears to be in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=testdisk&searchon=name&subword=1&version=all&release=all).

**Step 1**: Enable extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Install *testdisk*: ```
sudo aptitude update && sudo aptitude install testdisk
```

---

### Post by xxlbstripesxx on 2006-12-17
Ubuntu Dapper, and XP but when I attempt to boot into XP i get an error 13 and when I attempt to mount that and my shared FAT32 I get this:

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by aysiu on 2006-12-17
Are you using commands like these to mount your shared FAT32? ```
sudo mkdir /fatty
sudo mount -t vfat /dev/hda2 /fatty -o iocharset=utf8,umask=000
``` And, if so, and you're still getting that error, are you absolutely sure /dev/hda2 is FAT32? Can you also post the output of this command? ```
sudo fdisk -l
```

---

### Post by xxlbstripesxx on 2006-12-17
The installation directions worked perfectly. I am installing right now. Thank You very much.

---

### Post by xxlbstripesxx on 2006-12-17
OK so I ran TestDisk and before I proceed with analysis I get this : 

[COLOR="Blue"]Disk /dev/hda - 114470 MB - CHS 14593 255 63
Check current partition structure
     Partition                  Start        End    Size in sectors
 1 P Linux                    0   1  1   891 254 63   14329917
Invalid NTFS boot
 2 * HPFS - NTFS            892   0  1  3059 254 63   34828920
 2 * HPFS - NTFS            892   0  1  3059 254 63   34828920
 3 P Linux Swap            3060   0  1  3250 254 63    3068415
test_FAT : Boot sector doesn't have the endmark 0xAA55
 4 P FAT32                 3251   0  1 14592 254 63  182209230
 4 P FAT32                 3251   0  1 14592 254 63  182209230[/COLOR]

And afterward I get this:
[COLOR="Blue"]
     Partition               Start        End    Size in sectors
* Linux                    0   1  1   891 254 63   14329917
P Linux Swap            3060   0  1  3250 254 63    3068415
L FAT32 LBA             7450   1  1 14592 254 63  114752232 [ACERDATA][/COLOR]

What happened to my Windows Partition. I assume that I will need to reinstall Windows. What would be the most effective method of doing this for rebooting and is there any way to recover windows without formatting my entire harddrive and reinstalling. Thank You very much for your help.

---

### Post by xxlbstripesxx on 2006-12-17
I had just been using mount -a. Which gave me the error for both of them I just used hda2 to show you hda4 is my FAT32. I used the commands you gave me and I get this: 

[COLOR="Blue"]chris@chris-laptop:~$ sudo mkdir mnt
chris@chris-laptop:~$ sudo mount -t vfat /dev.hda4 /mnt -o iocharset=utf8,umask=000
mount: special device /dev.hda4 does not exist
[/COLOR]
my fdisk looks like this:

[COLOR="SeaGreen"]Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         892     7164958+  83  Linux
/dev/hda2   *         893        3060    17414460    7  HPFS/NTFS
/dev/hda3            3061        3251     1534207+  82  Linux swap / Solaris
/dev/hda4            3252       14593    91104615    b  W95 FAT32[/COLOR]

---

### Post by xxlbstripesxx on 2006-12-18
I was searching the forums again for any help and I came across this I was wondering if this might be extraordinarily similar to my problem given that I also have my NTFS drive as hda2. 
[http://ubuntuforums.org/showthread.php?t=297767&highlight=damaged+partition]("http://ubuntuforums.org/showthread.php?t=297767&highlight=damaged+partition")

I however backed up all of my important files so would I just go into gparted format my Ubuntu and NTFS drives and essentially switch them to make XP HDA1 and then just reinstall everything.

---

### Post by xxlbstripesxx on 2006-12-18
Can someone please help and tell me if this is an acceptable solution.

---

### Post by freebeer on 2006-12-18
> **xxlbstripesxx said:**
> 
[COLOR="Blue"]chris@chris-laptop:~$ sudo mkdir mnt
chris@chris-laptop:~$ sudo mount -t vfat /dev.hda4 /mnt -o iocharset=utf8,umask=000
mount: special device /dev.hda4 does not exist
[/COLOR]


Shouldn't the second line read:

```

sudo mount -t vfat /dev**/**hda4...

```

ie a "/" where you have a "." between dev and hda4?

---

### Post by xxlbstripesxx on 2006-12-19
THanks, I didn't even notice that but then I just get this error again.

mount: wrong fs type, bad option, bad superblock on /dev/hda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by xxlbstripesxx on 2006-12-19
Can someone please help me. Why doesn't my FAT32 partition mount.

---

