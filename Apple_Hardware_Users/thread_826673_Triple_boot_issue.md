---
title: "Triple boot issue"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by joselin on 2008-06-12
Hi,

I'm trying to set up a macbook santa rosa with triple boot and I have one issue that can't solve. I have installed windows (and configure it), then ubuntu and refit without issues.

But for now, I am able to start osx and ubuntu, but when I tried to start windows, something goes wrong and the system reboot itself. I can see the win xp loading image, then appear a message, that can't read (too fast for me) and reboot the machine.

If I try to install windows again the install cd can't recognize the partitions table, so can't do anything.

I know that windows runs without problems, because in the first steps i were able to restart it several times without issues.

So, the question is, can someone point me on how to repair windows install?

Regards.

---

### Post by prshah on 2008-06-12
> **joselin said:**
> but when I tried to start windows, something goes wrong and the system reboot itself. I can see the win xp loading image, then appear a message, that can't read (too fast for me) and reboot the machine.


Blue screen blues...

When you choose to start Windows, immediately keep tapping Ctrl and F8 _alternatively_. This will present you with a boot menu. In that, choose the option: "Disable automatic restart on failure."

Then choose to boot XP normally. When the boot fails, you will get a blue screen with the error messages ALL_IN_CAPITALS_WITH_UNDERSCORES.

Note that error message and post it back here for a fix.

---

### Post by joselin on 2008-06-12
Thanks for the tip, I didn't know it. Will try when arrive home and post the results.

---

### Post by cyberdork33 on 2008-06-12
Also check that the partition tables are synced in rEFIt.

---

### Post by joselin on 2008-06-12
> **prshah said:**
> Note that error message and post it back here for a fix.

This is the error I received:

PROCESS1_INITIALIZATION_FAILED

Could you please help me on it?

Regards

---

### Post by prshah on 2008-06-12
> **joselin said:**
> 
PROCESS1_INITIALIZATION_FAILED



This message usually means ntdll.dll file is not found. this file resides in the SystemRoot/system32 folder (typically c:\windows\system32\ntdll.dll). I assume that it cannot find it because the SystemRoot is not setup properly.

Boot into ubuntu, and post results of the following commands```
sudo fdisk -l
``` and the "boot.ini" file from the windows partition. Eg, if windows partition is /dev/sda2, then ```
cat /dev/sda2/boot.ini
``` If the above command returns an error or a blank output, you've probably got the wrong partition.

---

### Post by joselin on 2008-06-12
> **prshah said:**
> This message usually means ntdll.dll file is not found. this file resides in the SystemRoot/system32 folder (typically c:\windows\system32\ntdll.dll). I assume that it cannot find it because the SystemRoot is not setup properly.

Nop, ntdll.dll exists on that path.
$ ls -l WINDOWS/system32/ntdll.dll 
-rwxrwxrwx  1 jherran  staff  732672 Aug 19  2004 WINDOWS/system32/ntdll.dll

> Boot into ubuntu, and post results of the following commands```
sudo fdisk -l
``` and the "boot.ini" file from the windows partition. Eg, if windows partition is /dev/sda2, then ```
cat /dev/sda2/boot.ini
``` If the above command returns an error or a blank output, you've probably got the wrong partition.I'm writing from mac, so hope that helps.
$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            74.9 Gi    disk0s2
   3:       Microsoft Basic Data LINUX                   623.0 Mi   disk0s3
   4:       Microsoft Basic Data                         59.9 Gi    disk0s5
   5:                 Linux Swap                         2.6 Gi     disk0s6
   6:       Microsoft Basic Data WINDOWS                 10.8 Gi    disk0s4


$ cat boot.ini 
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Any ideas?

Regards

---

### Post by cyberdork33 on 2008-06-12
> **joselin said:**
> ```

$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            74.9 Gi    disk0s2
   3:       Microsoft Basic Data LINUX                   623.0 Mi   disk0s3
   4:       Microsoft Basic Data                         59.9 Gi    disk0s5
   5:                 Linux Swap                         2.6 Gi     disk0s6
   6:       Microsoft Basic Data WINDOWS                 10.8 Gi    disk0s4
```
If you are going to use the OS X side, please, first, make sure to sync partitions in rEFIt. and post the partition information using the partition report tool in your Utilities folder (part of rEFIt). Thanks.

From what you have posted so far, it looks like your windows partition is #6. This will not work.

---

### Post by prshah on 2008-06-13
> **joselin said:**
> 
   4:       Microsoft Basic Data                         59.9 Gi    disk0s5
   6:       Microsoft Basic Data WINDOWS                 10.8 Gi    disk0s4

$ cat boot.ini 
multi(0)disk(0)rdisk(0)[color=red]partition(4)[/color]\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect



I don't know how Mac interprets partitions, but I'm guessing that partitions 4 & 5 are your windows partitions. (or maybe, as suggested by cyberdork33, partition 6). Your boot.ini is set to find windows files on partition number 4, maybe you need to try 5 or 6 in it's place.

I also know that there is some booting limitation in Windows, as suggested by cyberdork, where it will not boot if it is beyond the 32Gb limit. However, this problem was in earlier versions of Windows, I don't know if it has been fixed XP onwards.

The order the partitions appear on the hard disk is important for this. Can you post a graphical representation of the partitioning; something like what gparted shows in ubuntu?

---

### Post by joselin on 2008-06-13
Don't know why, but now the windows starts working without issues. And yes, win is on partition #6, and as I told before, works.

I start my mac with the xp cd inserted and boot that cd from refit. Before yesterday the xp install never saw the windows partition, but yesterday it did it and let me install windows again. After the reinstallation all went fine and boot windows every time without problems.

Please, don't ask me why, because I don't know what I did (in other way that other times).

Thanks all of you for your help, were another point of view and let me try new things.

Regards

---

### Post by cyberdork33 on 2008-06-13
On the Mac, windows will not boot if it is on a partition > #4. It is a limitation of the emulated MBR.

I will assume that if you have it working, you are booting off partition #4 as suggested.

---

### Post by joselin on 2008-06-13
Don't know why, but the thing is on my partition table windows is on partition #6 and don't know where the emulated mbr is installed. Partitions #3, #4 and #5 are for linux, so I supposed that windows does not boot from there. Who knows!!!

---

### Post by cyberdork33 on 2008-06-13
> **joselin said:**
> Don't know why, but the thing is on my partition table windows is on partition #6 and don't know where the emulated mbr is installed. Partitions #3, #4 and #5 are for linux, so I supposed that windows does not boot from there. Who knows!!!
You would get much better information about your partitions if you use the rEFIt tools.

---

