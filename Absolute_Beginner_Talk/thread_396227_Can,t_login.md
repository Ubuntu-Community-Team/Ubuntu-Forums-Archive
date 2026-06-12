---
title: "Can,t login"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by antoz on 2007-03-29
Unable to login after installing Dapper. Below is the message I am getting. (this install has been a struggle)

[COLOR="Red"]? You home directory is listed as:
"/Home/my name"
but it does not appear to exist. Do you want to log in with /(root) directory as your home directory.
It is unlikely anything else wil work unless you use a failsafe session
NO - YES[/COLOR]

My root partition is sda3, Home partition is sda8, swap is sda7

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ sudo mkdir /media/sda8
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda3 /media/sda8
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6494    52163023+   7  HPFS/NTFS
/dev/sda2            6495       29049   181173037+   f  W95 Ext'd (LBA)
/dev/sda3           29050       30377    10667160   83  Linux
/dev/sda5            6495       24026   140825758+   7  HPFS/NTFS
/dev/sda6           24027       26576    20482843+   b  W95 FAT32
/dev/sda7           26577       26917     2739051   82  Linux swap / Solaris
/dev/sda8           26918       29049    17125258+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19678   158063503+   7  HPFS/NTFS
/dev/sdb2           19679       24321    37294897+   5  Extended
/dev/sdb5           19679       24321    37294866    7  HPFS/NTFS

Disk /dev/sdd: 257 MB, 257948672 bytes
33 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         243      251887    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(249, 32, 63) logical=(242, 10, 58)

[COLOR="Red"]ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
ubuntu@ubuntu:~$[/COLOR]

If there is anyone who could explain my problem and my strange fstab it would be great. Thanks in advance, A

---

### Post by taurus on 2007-03-29
Boot into a recovery mode from GRUB menu and post the output of this command here.

```
ls -la /home
```

---

### Post by Bachstelze on 2007-03-29
Your root and home partitons are not in fstab, neither is /proc. This is really bad, you should at least add those three.

---

### Post by antoz on 2007-03-29
Thank you taurus for looking at this. 
This what I get:
drwxr-xr 2 root root 4096 Mar 27 10:38
drwxr-x 23 root root 4096 Mar 27 10:38

there is also a message before I entered the command:

"Warning your /etc/fstab does not contain fsk passno field. I wil Kludge around things for you, but you should fix your /etc/fstab file as soon as you can"

I was using the live CD so had to boot again + I am not that fast with my fingers

---

### Post by antoz on 2007-03-29
HymnToLife I have no idea why they are not there  thought this was just going to be a simple install, had a lot of trouble as well with bits missing in the menu lst I am learning as I go along (je suis perdu) A

---

### Post by antoz on 2007-03-29
I attached a sreen shot for a bit more information, I think at the end I will probably just have to reinstall because at the moment I don't really know what I am doing, but will persist with it for an bit longer. A

---

### Post by antoz on 2007-03-30
Got there finally; was able to login for the first time today. The problem was the fstab and thanks to **confused **(on an other thread I had started earlier when I had grub and boot problems) he more or less constructed it for me all I had to do is paste it in.

[http://http://ubuntuforums.org/showthread.php?t=394493]("http://http://ubuntuforums.org/showthread.php?t=394493")

Again thanks everybody this has been a good leaning experience, Ubuntu really is a great community. I am sure i will be back with other problems and  hope that even with my limited knowlege that I can help out someone else in the future. Cheers, A.

---

