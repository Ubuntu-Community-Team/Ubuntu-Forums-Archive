---
title: "Grub refuses to install after parted"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2010-01-31
Hi.

I ran a Gparted to reduce the OSX partition and now when booting ubuntu it tells me that there is no operating system.
 
I tried to reinstall grub from the live cd, but this is what I get:

```
root@ubuntu:/# mount /dev/sda3 /mnt
root@ubuntu:/# grub-install /dev/sda3 --root-directory=/mnt --recheck
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/mnt/boot/grub/core.img' correctly

```I need help.

Thanks.
Luigi.

---

### Post by pastalavista on 2010-01-31
> **luigi.viggiano said:**
> Hi.

I ran a Gparted to reduce the OSX partition and now when booting ubuntu it tells me that there is no operating system.
[snip]

Thanks.
Luigi.

Boot into the Ubuntu CD and run in terminal ```
sudo fdisk -l
```

and post the output.

---

### Post by linuxopjemac on 2010-01-31
same sort of problem [here]("http://ubuntuforums.org/showthread.php?t=1392604"). You can try to delete boot codes in the MBR:

I would try to install the bootloader in the MBR (/dev/sda) and first make it clean:
```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

You might also first want to try to set a boot flag on the Ubuntu root from the liveCD (gparted)

---

### Post by luigi.viggiano on 2010-01-31
> **pastalavista said:**
> Boot into the Ubuntu CD and run in terminal ```
sudo fdisk -l
```and post the output.


```
root@ubuntu:/# sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002517

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        2575    20478867+  af  HFS / HFS+
/dev/sda3            2576       37844   283298242+  83  Linux
/dev/sda4           37845       38914     8587345   82  Linux swap / Solaris

```

---

### Post by luigi.viggiano on 2010-01-31
> **linuxopjemac said:**
> same sort of problem [here]("http://ubuntuforums.org/showthread.php?t=1392604"). You can try to delete boot codes in the MBR:

I would try to install the bootloader in the MBR (/dev/sda) and first make it clean:
```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```You might also first want to try to set a boot flag on the Ubuntu root from the liveCD (gparted)

I set the boot flag on /dev/sda3 and I tried

```
root@ubuntu:/# sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.4e-05 s, 21.3 MB/s
root@ubuntu:/# grub-install /dev/sda --root-directory=/mnt --recheck 
grub-probe: error: Cannot find a GRUB drive for /dev/sda3.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

It didn't work. 

I tried to dd also /dev/sda3 with same result :(

---

### Post by linuxopjemac on 2010-01-31
sorry forget it, I didn't read well enough..

---

### Post by linuxopjemac on 2010-01-31
try this

```
sudo sh -c "echo '(hd0) /dev/sda' > /boot/grub/device.map && cd /dev && mknod sda b 202 0"
```

from [here]("http://orangesquash.org.uk/2009/02/16/now-running-lenny-and-a-workaround-for-a-grub-bug/").

I have no idea what it does to be honest...at your own risk..

---

### Post by linuxopjemac on 2010-01-31
the problem is in /boot/grub/device.map

You might have to edit it manually if the former code does not work..I think it should say:

```
jeroen@jeroen-ubuntu:~$ cat /boot/grub/device.map 
(hd0)	/dev/sda

```

---

### Post by pastalavista on 2010-01-31
I don't understand how the new grub works yet, but you can fix your problem (probably) if you do what I've done several times. With the live CD, install Ubuntu again in MANUAL mode and at the partition editor, UNCHECK all the 'format' boxes. Nothing gets erased but you start fresh again and maybe grub works this time...

---

