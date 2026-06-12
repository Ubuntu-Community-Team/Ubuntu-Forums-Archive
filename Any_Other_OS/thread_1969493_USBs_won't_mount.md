---
title: "USBs won't mount"
date: 2012-04-29
forum: Any Other OS
---

### Post by sleepee on 2012-04-29
so i have this problem that came up out of the blue.  i have no idea what possibly could have caused it.
i can't mount usb's.  they used to automount just fine by themselves, but now they don't mount automatically and i can't mount them manually either.

this is the command i run when i try to mount usb's manually.

```

sleepee@sleepee-laptop:/dev$ sudo mount /dev/sdb/ /media/USB/

```

i run that command and it just sorta stays stuck there..
i know it doesn't take more than 5 seconds to mount, so when i pull the usb after i get tired of waiting, i get this

```
mount: special device /dev/sdb does not exist
```

something similar happens when i run fdisk -l
```

sleepee@sleepee-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44c64793

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   495666353   247628377    7  HPFS/NTFS/exFAT
/dev/sda3       495669634   976559219   240444793    5  Extended
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)
/dev/sda5       956076408   976559219    10241406   82  Linux swap / Solaris
/dev/sda6       495669636   557102069    30716217   83  Linux
/dev/sda7       557102133   956076344   199487106   83  Linux

Partition table entries are not in disk order
```

if i run that command with the USB in, i get that output, but the terminal won't give me a prompt until i remove the USB.
running the command without the USB will give me the same output and will immediately give me prompt too..

gparted won't recognize the USB partition either...

i'm kind of a newbie so i don't know what else to try.  i just can't manage for my laptop to see my usb's.

*Correction*
My Linux install won't recognize my USB's.  My windows partition sees my USB just fine.
BTW, i'm running 64 bit Mint 12 (based on Oneiric) if that matters

Please help!
TIA

---

### Post by Perfect Storm on 2012-04-30
Moved to Other OS/Distro Talk.

---

### Post by The Rnegade on 2012-05-02
> **sleepee said:**
> so i have this problem that came up out of the blue.  i have no idea what possibly could have caused it.
i can't mount usb's.  they used to automount just fine by themselves, but now they don't mount automatically and i can't mount them manually either.

this is the command i run when i try to mount usb's manually.

```

sleepee@sleepee-laptop:/dev$ sudo mount /dev/sdb/ /media/USB/

```i run that command and it just sorta stays stuck there..
i know it doesn't take more than 5 seconds to mount, so when i pull the usb after i get tired of waiting, i get this

```
mount: special device /dev/sdb does not exist
```something similar happens when i run fdisk -l
```

sleepee@sleepee-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44c64793

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   495666353   247628377    7  HPFS/NTFS/exFAT
/dev/sda3       495669634   976559219   240444793    5  Extended
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)
/dev/sda5       956076408   976559219    10241406   82  Linux swap / Solaris
/dev/sda6       495669636   557102069    30716217   83  Linux
/dev/sda7       557102133   956076344   199487106   83  Linux

Partition table entries are not in disk order
```if i run that command with the USB in, i get that output, but the terminal won't give me a prompt until i remove the USB.
running the command without the USB will give me the same output and will immediately give me prompt too..

gparted won't recognize the USB partition either...

i'm kind of a newbie so i don't know what else to try.  i just can't manage for my laptop to see my usb's.

*Correction*
My Linux install won't recognize my USB's.  My windows partition sees my USB just fine.
BTW, i'm running 64 bit Mint 12 (based on Oneiric) if that matters

Please help!
TIA
  
I have this too. for me it was a hardware error, by plugging the usb drive into a diffrent port on my pc it automounted. give that a try, it might work

---

### Post by sleepee on 2012-05-03
yea, that's what i thought at first too.  my laptop has 4 usb ports and i tried them all, but with no luck.
but i don't think it's hardware anyway, because any time i boot up windows on the same computer (which is very, very rarely lol) it'll work just fine.
also, i've plugged in my android tablet and it'll get recognized.... ususally...  sometimes plugging in the tablet gives me problems too..
i don't know what it is, but i'm probably going to do a re-install when the new linux mint comes out anyway... but i kinda wanted to figure it out before i reinstall just to see what exactly happened.

---

### Post by Dlambert on 2012-05-04
Try using disk utility? And maybe the drive is formatted to a filesystem not linux compatable? Just my two cents.

---

### Post by linuxmatt7 on 2012-05-06
The same is happening to me on my dad's Linux Mint laptop. I have filed a bug report nothing yet. I have asked this question many times in the Linux Mint forums, but no helpful answers yet.

---

### Post by sleepee on 2012-05-20
> **Dlambert said:**
> Try using disk utility? And maybe the drive is formatted to a filesystem not linux compatable? Just my two cents.

I don't think so.  I've formatted it to fat32... multiple times... with multiple usb drives.

I don't know. this is really weird.  I'm thinking it has to be Mint-related because, besides Windows and Puppy Linux on the same computer being able to read the USB, I just bought an Asus Eee PC netbook and put Mint 12 on it and the exact same thing happens!
I think I might try and see if I can mount it using Ubuntu... or maybe try the Mint 13 RC and see if they've fixed it.

---

### Post by sleepee on 2012-05-20
> **linuxmatt7 said:**
> The same is happening to me on my dad's Linux Mint laptop. I have filed a bug report nothing yet. I have asked this question many times in the Linux Mint forums, but no helpful answers yet.

Have you tried reading the USB on that computer with a different OS?  like Windows or some other Linux distro?
Because right now, I've got 3 machines with Mint and all 3 have this same problem.
Maybe they'll fix it with Mint 13?  It is an LTS release after all...

---

### Post by TransitMan on 2012-05-21
> **sleepee said:**
> Have you tried reading the USB on that computer with a different OS?  like Windows or some other Linux distro?
Because right now, I've got 3 machines with Mint and all 3 have this same problem.
Maybe they'll fix it with Mint 13?  It is an LTS release after all...

Check and see if you have pmount installed. If not, install it.
It will auto-mount usb devices not listed in /etc/fstab
You can find pmount in Synaptic, or in terminal:
```
sudo apt-get install pmount
```

---

