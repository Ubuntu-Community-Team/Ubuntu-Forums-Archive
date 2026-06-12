---
title: "Failed to mount /dev/hdb1"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by MadsRH on 2008-01-05
Hi
I know this topic has be posted many times, but I simply can't find the answer to my question. My question is, why can't I access my 160 Gb XP (NTFS) harddrive from Ubuntu 7.10?
The XP harddrive was installed as slave after the Ubuntu installation was finished.


```
sudo fdisk -l

Disk /dev/hda: 10.2 Gb, 10246053888 byte
255 heads, 63 sectors/track, 1245 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac21ac21

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hda1   *           1        1187     9534546   83  Linux
/dev/hda2            1188        1245      465885    5  Udvidet
/dev/hda5            1188        1245      465853+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 Gb, 160041885696 byte
78 heads, 14 sectors/track, 286247 cylinders
Units = cylindre of 1092 * 512 = 559104 bytes
Disk identifier: 0xd7a0d7a0

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hdb1   *           1      286246   156290309    7  HPFS/NTFS

Disk /dev/sda: 2063 Mb, 2063073280 byte
16 heads, 32 sectors/track, 7870 cylinders
Units = cylindre of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1               1        7870     2014704    b  W95 FAT32

```

The XP harddrive is visible like the other drives, but when I try to access the drive I get this:

**$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/hdb1': Operation not suppoted Mount is denied because NTFS is marked to be in use........**

Can anyone help me? :(

---

### Post by exneo002 on 2008-01-05
I hate to simplify your problem but hdb1 is an external hd if I am correct 
1. the most simple solution If it is a segate It wont work segate imposed power saving features that shut the hd down after a couple mintutes of activity this means one that it would be near impossible to make a linux install to it and two that linux cant keep up with the process so your hd would shut down 
2. beyond that you might need a propietary driver to run it  
3. It might be somthing what segat did or a hardware incompatibility 
4. you might wnt to bash up your box bourne again shell ha I don't know that many codes off the top of my head because their are many great lists online google is your friend

---

### Post by MadsRH on 2008-01-05
It is NOT an external drive. It's a Samsung harddrive!

---

### Post by taurus on 2008-01-05
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
[COLOR="Red"](And if you get an error message about it didn't shutdown cleanly, then use the force option to mount it.)
(Again, only run the next command if the previous one produces a warning message.)[/COLOR]
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
df -h
```

---

### Post by MadsRH on 2008-01-05
WOW, you're right! I got an error message, but it work out! Thanks a lot, and thank you for you're fast reply

Here is what I got:

```
 sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

madsrh@madsrh-desktop:~$ df -h
Filsystem            Størr Brugt  Tilb Brug% Monteret på
/dev/hda1             9,0G  3,6G  5,0G  43% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             2,0G  902M  1,1G  46% /media/KINGSTON
/dev/hdb1             150G  143G  7,1G  96% /media/hdb1

```

Thanks again :)

---

