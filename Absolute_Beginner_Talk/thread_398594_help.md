---
title: "help"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-04-01
i have 2 HDD. this is how it looks from gparted :

                                         dev/sda
[-------------------------------------unallocated---------------------------------------]

                                         dev/sdb
[----dev/sdb1(ext3)----|---------------------------dev/sdv2(ext3)-----------]

i have two partritons on dev/sda which gparted can't detect. one of them is windows. I have installed windows after installing Ubuntu and i have done the following 
```

grub
grub> find /boot/grub/stage1
grub> root (hd1, 0)
grub> setup (hd0)
grub> quit

```
to retrive the GRUB. One i have retrived it i can select Windows, but i get an error that the device can't be detected ( possibly 'cause the location of Win changed  ). So how can i know the location i need to insert in GRUB's menu.lst ?
here's my current menu.lst :
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
help please.

---

### Post by Sasa_Ivanovic on 2007-04-01
ok i know that this partrition with Windows is called "sda5" how can i transfer that to (hd?,?)

---

### Post by Sasa_Ivanovic on 2007-04-01
Now i get the error "error 13 : unsupported executable format", when i try to select windows in GRUB menu....
and i know Windows worked just before i entered that code above to retrive GRUB, there must be a way to solve this.

---

### Post by nixclusive on 2007-04-01
Looks like you are waging a one man stand here!! is that windows vista?

---

### Post by Sasa_Ivanovic on 2007-04-01
nope, XP pro

---

### Post by mikeyphi on 2007-04-01
I might be wrong...but I think that installing windows after linux overwrites the Grub....
In the short term you can access the windows drive via the BIOS boot selection.

---

### Post by mikeyphi on 2007-04-01
If you haven't already - try the suggestions at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows/](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows/)  there should be something there to get you going again!

---

### Post by Sasa_Ivanovic on 2007-04-01
if you haven't noticed i have allready done that in order to restore GRUB. But now when GRUB is restored i can boot Ubuntu but not Windows. In case you have been reading at all, but thanks anyways.

---

### Post by mikeyphi on 2007-04-01
> **Sasa_Ivanovic said:**
> ok i know that this partrition with Windows is called "sda5" how can i transfer that to (hd?,?)

It would seem that, on your system, in 'grubspeak' it should translate to hd0,4

---

### Post by Sasa_Ivanovic on 2007-04-02
i just changed my "menu.lst" to
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
i'm gonna post the results now...

---

### Post by Sasa_Ivanovic on 2007-04-02
i get "invalide device requested", but thanks anyways...

---

### Post by Sasa_Ivanovic on 2007-04-02
i might know what's the problem. here's what
```
sudo fdisk -lu
```
returned
```

omitting empty partition (5)

Disk /dev/sda: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240119615 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   240107489   120045712+   f  W95 Ext'd (LBA)
/dev/sda2   *    52837785   240107489    93634852+   b  W95 FAT32
/dev/sda5           16191    52837784    26410797    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    87891614    43945776   83  Linux
/dev/sdb2        87891615   303419654   107764020   83  Linux
/dev/sdb3       303419655   312576704     4578525    f  W95 Ext'd (LBA)
/dev/sdb5       303419718   312576704     4578493+  82  Linux swap / Solaris
sasa@Kanta:~$ 

```
now if you can notice the boot isn't set on sda5. i have read that windows has to be on the first partrtion in order to boot. and that you can go around this if you edit "boot.ini".
where can i find this boot.ini ?

---

### Post by Sasa_Ivanovic on 2007-04-02
here's the quote :
"It is usual to expect Windows to be allocated the partition number 1, and remain that way, even if you 'move' it with partitioning software to the other end of your disk.
If Windows is allocated a different partition number, either accidentally or on purpose, you just need to edit boot.ini with the changes and it will usually boot up fine."

---

### Post by mikeyphi on 2007-04-02
You need to be in Windows and use the 'bootcfg' command. It is normally done when in the 'Recovery Console'
I suggest you Boot into Windows (if you can) and read the full instructions by typing 'Bootcfg' into the Help and Support Centre screen

---

### Post by zvacet on 2007-04-02
[http://ubuntuforums.org/showthread.php?t=398876]("http://ubuntuforums.org/showthread.php?t=398876")
And please don´t use that kind of words in tags anymore.

---

