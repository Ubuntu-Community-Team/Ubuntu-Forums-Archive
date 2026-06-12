---
title: "[SOLVED] Sometimes my other NTFS harddrives don't show"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-07-08
Well everything ran perfectly untill about two or three days ago when I noticed that my 200GB and 80GB NTFS formated hard drives did not always show on Ubuntu. I searched in the Places>Computer
Previously, the harddrives mounted automatically but now they only show occasionally... HELP!!

---

### Post by taurus on 2007-07-08
What are the output of these commands from a terminal?

```
df -h
sudo fdisk -l
cat /etc/fstab
```

---

### Post by waggygee on 2007-07-08
> **taurus said:**
> What are the output of these commands from a terminal?

```
df -h
sudo fdisk -l
cat /etc/fstab
```

georg@georg-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              37G   20G   15G  57% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  112K  506M   1% /proc/bus/usb
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
georg@georg-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4787    38451546   83  Linux
/dev/hdb2            4788        4998     1694857+   5  Extended
/dev/hdb5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24320   195350368+   7  HPFS/NTFS

Now, Im no scientist but it appears that all my hard drives are showing here. Why cant I access them?:confused:

---

### Post by taurus on 2007-07-08
But how do you mount those ntfs filesystems. through /etc/fstab?

```
cat /etc/fstab
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by waggygee on 2007-07-08
I had a look at that automatic way (this is what I did initialy to get my hard drives running automatically). This time when I tried it I got this:

georg@georg-desktop:~$ sudo mv /etc/fstab.orig /etc/fstab
mv: cannot stat `/etc/fstab.orig': No such file or directory
georg@georg-desktop:~$ sudo umount /media/<mount point>
bash: syntax error near unexpected token `newline'
georg@georg-desktop:~$ sudo mv /etc/fstab.orig /etc/fstab
mv: cannot stat `/etc/fstab.orig': No such file or directory

Is there a way I can make the '/etc/fstab.orig' directory myself?

---

### Post by taurus on 2007-07-08
What's the output of 

```
ls -la /etc/fstab*
```

---

### Post by Teh Dust on 2007-07-08
Also, if windows is installed on any of your NTFS drives and you failed to shut down properly, you will have problems mounting. You may want to try downloading the NTFS Configuration Tool from Synaptic or Add/Remove.

---

### Post by michaelzap on 2007-07-08
This has happened to me several times. Each time I just booted back into Windows and shut down normally and the drives appeared again in Ubuntu. Maybe that will work for you, too.

---

### Post by waggygee on 2007-07-08
> **taurus said:**
> What's the output of 

```
ls -la /etc/fstab*
```

-rw-r--r-- 1 root root 627 2007-07-08 19:19 /etc/fstab
-rw-r--r-- 1 root root 749 2007-07-08 17:28 /etc/fstab.edgy
-rw-r--r-- 1 root root 750 2007-07-08 19:19 /etc/fstab.pre-ntfs-config
-rw-r--r-- 1 root root  37 2007-04-15 13:48 /etc/fstab.pre-uuid

Is what I get

---

### Post by taurus on 2007-07-08
As you can see from the output, there is no /etc/fstab.orig.  So, you could use the /etc/fstab.pre-ntfs-config.

```
sudo cp /etc/fstab /etc/fstab.bak
sudo cp /etc/fstab.pre-ntfs-config /etc/fstab
```
Then reboot.

---

### Post by snobby500 on 2007-07-08
i had the same problem, i did the same as michaelzap, boot into windows, and let it shut down properly using the shut down button, then boot into ubuntu and see what happens, that might help, u migh talso want to download the tool the other guy said - the ntfs configuration tool, if you type in ntfs in add remove programs it will come up first in list i think, and try unmounting and remounting your hardrive, im not sure if u need the tool for this, but that is how i solved the prob, i think i read somewhere that the problems happens because windows hasnt unmounted the drive, so this means that ubuntu cant mount it, but a successful shutdown in windows will make it unmount the hard drive, hope this helps.

---

### Post by waggygee on 2007-07-08
I feel so stupid. After shutting Windows down properly the harddrives mounted properly! Thanks everyone!

---

### Post by linaux on 2007-07-08
Don't feel stupid. Sometimes when something unsettling happens, it can
be difficult (for the person experiencing the problem) to see the solution, even
an obvious one. Luckily, there are a lot of helpful people here.

---

### Post by snobby500 on 2007-07-09
dont feel stupid lol, sometimes things are just really simple, but its hard to see it :) plus, tht wud make me stupid as i had same problem :P

---

