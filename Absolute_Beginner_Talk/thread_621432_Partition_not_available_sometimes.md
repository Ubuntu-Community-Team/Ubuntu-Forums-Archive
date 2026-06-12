---
title: "Partition not available sometimes"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-11-23
When I start up Ubuntu, the partition is available sometimes, I have to be lucky. This has become quite the problem the last weeks because nowadays it won't even show up at all. This partition is NTFS and made to store things unlike my Windows partition which actually shows up about every time. Maybe this has something to do with the computer checking for the hardware everytime by the manufacturer screen which takes up a lot of time :confused:

Anyways, any ideas?

---

### Post by jingo811 on 2007-11-23
That's weird.  Dunno where to start but doing this in terminal and pasting the outputs in here should be a good conversation starter.

```
sudo fdisk -l
```
```
sudo df -h
```

---

### Post by laidback on 2007-11-23
Have had an issue with my USB drive that may be similar. In Feisty my USB hdd partitions mounted automatically until I created the 7th one (I think it was 7th). I could mount it by hand but not via the automatic system. When I tried Gutsy it did mount automatically. As I haven't had much experience with Gutsy and still don't use it as my default system I cannot say that moving the Gutsy solves it. But if you're not using Gutsy yet it might be worth a try.

---

### Post by disturbedite on 2007-11-23
i had the same thing recently (yet again) on hardy.  my second hdd/partition was not assigned by UUID when i installed kubuntu unlike my / partition/hdd.  so i found the drive's/partition's UUID using this:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
and assigned it to the correct UUID in fstab.  it seems to have fixed the occasional disappearance of the partition...

---

### Post by kcirtap on 2007-11-24
When I type sudo fdisk -l I get the following:

> 
Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x27ec27eb

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       35057   250879072+   f  W95 Utökad (LBA)
/dev/sda3           35058       38789    29977290   83  Linux
/dev/sda4           38790       38913      996030   82  Linux växling / Solaris
/dev/sda5            3825       35057   250879041    7  HPFS/NTFS

Disk /dev/sdb: 400,0 GB, 400088457216 byte
16 huvuden, 63 sektorer/spår, 775221 cylindrar
Enheter = cylindrar av 1008 · 512 = 516096 byte
Diskidentifierare: 0xf11c84a1

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1      775218   390709840+   7  HPFS/NTFS


And when I type sudo df -h I get:

> 
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda3              29G  5,7G   22G  22% /
varrun                1,5G   92K  1,5G   1% /var/run
varlock               1,5G     0  1,5G   0% /var/lock
udev                  1,5G   68K  1,5G   1% /dev
devshm                1,5G     0  1,5G   0% /dev/shm
lrm                   1,5G   34M  1,5G   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              30G   15G   16G  49% /media/sda1
/dev/sda5             240G  2,9G  237G   2% /media/sda5



> **disturbedite said:**
> i had the same thing recently (yet again) on hardy.  my second hdd/partition was not assigned by UUID when i installed kubuntu unlike my / partition/hdd.  so i found the drive's/partition's UUID using this:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
and assigned it to the correct UUID in fstab.  it seems to have fixed the occasional disappearance of the partition...

Ok, I'll try that and see if it fixes the problem.

---

### Post by jingo811 on 2007-11-24
Sounds like a distro specific problem to me.  Ubuntu Feisty 7.04 has been used by public since April 2007 Ubuntu Gutsy 7.10 has been used by public since October 2007 that's less than a month of existence.  Feisty is stable Gutsy is well you do the math.

---

