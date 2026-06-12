---
title: "[SOLVED] External Hard Drive: Unable to mount the selected volume"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by skwon11 on 2008-02-23
Moderator, OK to move wherever you feel fit.

I have a Seagate USB external hard drive broken into 2 volumes.  Recently upon rebooting only one of the volumes is readable and writable to.  You can see both volumes but when you go to mount the unviewable one (GUI mount) you get the following:

Unable to mount the selected volume
error: directory /media/disk1s1_1 is not empty

error: could not execute pmount


I'm confused.  Can anybody tell me what this means and how to fix it?  The drive is for backup purposes only.  My internal drive is Ubuntu only... no Windows partition, etc., etc..  Thank you.

---

### Post by taurus on 2008-02-23
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by lost09 on 2008-02-23
I recently suffered a similar problem with a Seagate drive. If you have access to a Windows system, connect the drive, check it's Properties, and ensure that Autoplay is not enabled.

---

### Post by skwon11 on 2008-02-23
As requested

```

skwon11@skwon11-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78136128    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2            9728       19458    78154713    b  W95 FAT32
Partition 2 does not end on cylinder boundary.
skwon11@skwon11-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   21G   13G  63% /
varrun                375M   92K  375M   1% /var/run
varlock               375M  4.0K  375M   1% /var/lock
udev                  375M  132K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
lrm                   375M   19M  357M   5% /lib/modules/2.6.15-51-386/volatile
/dev/sda2              75G   16G   60G  21% /media/DISK1S1_2

```

---

### Post by taurus on 2008-02-23
What happens if you try to mount it, /dev/sda1, by hand from a terminal?

```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
df -h
```

---

### Post by skwon11 on 2008-02-24
Worked like a charm.  Thank you.  I would like to understand what happened though vs. just using your commands.  If you have the time to spare... let me know.  Thanks again.

---

### Post by robertchahine on 2008-02-24
hey there, i have a ipod, when i connect it to the pc, the ubuntu find it, and read it as two volumes. when i click open i have the following error "**unable to mount media**" "there is probably no media in the drive", 
plz help and thank you.

---

### Post by skwon11 on 2008-02-29
Unrelated,

How do I close this thread?  Sorry.

---

### Post by mt330404 on 2008-03-27
I had a problem where I took my (NTFS formatted) external HD, used it on a Windows computer to transfer some music files.. tried to safely remove it but the Windows computer said it was still in use (even though it wasn't, NO programs were running-- go figure).. anyway, I unplugged it unsafely, then when I tried to plug it back into my Ubuntu computer, i got the "unable to mount" problem. Tried to force-mount it in terminal but no luck. All I ended up having to do was plug my external HD into a windows computer (I chose a diff. one from before in case I got the same problem), it recognized my files so nothing was lost. I safely removed the external HD with no problems, plugged it back into the Ubuntu computer and it was then able to mount. SO.. if you're like me and you use your external HD on a lot of diff. computers, you might have run into this problem. This is what I did to solve it without any major problems.

---

