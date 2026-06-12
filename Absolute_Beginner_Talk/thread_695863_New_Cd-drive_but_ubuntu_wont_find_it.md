---
title: "New Cd-drive but ubuntu wont find it"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2008-02-13
I changed my CD reader and the bios find it without problem, thing is that ubuntu wont find it, Do i really need to reinstall ubuntu to be able use the CD?

---

### Post by 1875 on 2008-02-13
You will have to find the name your Cd-rom has been given and edit your fstab accordingly.


[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

Should tell you what you need to know.

---

### Post by sam0t on 2008-02-13
I have the exact same problem, I havent booted up ubuntu in a long while and now my cd-rom is missing. I know something about fstab, and there is my old cdrom mounting routine. 

Maybe my cd-rom driver changed somehow as I flashed in Windows, what command to use to find out current name of the cdrom ? fdisk -l does not show it :/

edit:

My Fstab for cdrom seems rather ordinary:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

edit2:

Heres some stuff from my /var/log/syslog

hda: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive

So clearly hda still is my dvd driver :/

---

### Post by SpinningAround on 2008-02-14
I think i'm still to new to linux, to understand how to change this. I can see that there is a cd0 in /etc/fstab but I don't know if it's the correct one or how i find the correct one, since there is no UUID nr.

Possible some less generall guide?

---

### Post by PmDematagoda on 2008-02-14
Post the output of:-
```
lshw
```

---

### Post by Cypher on 2008-02-14
At the console type the following
```

dmesg | grep -i hd

```
This will you tell you if the CD Drive was indeed found..

---

### Post by SpinningAround on 2008-02-14
> **PmDematagoda said:**
> Post the output of:-
```
lshw
```

[PHP]
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   product: HL-DT-ST CD-ROM GCR-8522B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capabilities: packet

[/PHP]

---

### Post by SpinningAround on 2008-02-15
> **Cypher said:**
> At the console type the following
```

dmesg | grep -i hd

```
This will you tell you if the CD Drive was indeed found..
[PHP]
dator@dator2:~$ dmesg | grep -i hd
[   27.776304]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:DMA
[   27.776323]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   28.919217] hdb: HL-DT-ST CD-ROM GCR-8522B, ATAPI CD/DVD-ROM drive
[   29.395081] hdc: Hitachi HDS721616PLAT80, ATA DISK drive
[   30.140488] hdb: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[   30.163069] hdc: max request size: 512KiB
[   30.163220] hdc: 312581808 sectors (160041 MB) w/7376KiB Cache, CHS=19457/255/63, UDMA(133)
[   30.163365] hdc: cache flushes supported
[   30.163438]  hdc: hdc1 < hdc5 hdc6 >
[   42.565674] Adding 2273124k swap on /dev/hdc5.  Priority:-1 extents:1 across:2273124k
[   42.958645] EXT3 FS on hdc6, internal journal

[/PHP]

---

### Post by PmDematagoda on 2008-02-15
Try this:-

1) Open the fstab file for editing using:-
```
gksudo gedit /etc/fstab
```

2) Create a folder called cdrom0 in /media:-
```
sudo mkdir /media/cdrom0
```

3) Add this line:-
```
/dev/hdb1 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Then boot Ubuntu and see if your CD-ROM gets detected.

---

### Post by SpinningAround on 2008-02-16
Thanks :D Ubuntu find the CD now, but there are two things that don't seem to work correct.

1. If I mount a cd, can't i eject the cd with the buttom on the drive, the only way to do this is with selecting "eject" in the meny when you right click on the desktop icon.

2. Unsure about this is wrong. It mount the cd /media/"name of cd" instead of /media/cdrom0 cdrom0 simply don't point at the cd.

When nothing is mounted is there two folders in /media
cdrom (with an arrow)
cdrom0

when a cd is mounted is there tree
cdrom (with an arrow)
cdrom0
"name of cd"

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc6
UUID=965360e6-d016-4eb1-a1ab-bc6af6d1f8e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=52de8a77-a36d-4862-a349-1996abe9b6da none            swap    sw              0       0
/dev/hdb1 /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

