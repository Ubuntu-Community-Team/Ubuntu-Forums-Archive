---
title: "Non-mounting harddrive"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by dmitrijledkov on 2007-10-18
I used to have following partitions in total 250GB (but less cause this is multiples of 10)
1) About 60GB with carbon copy of my internal harddrive HFS+

2) About 120GB with Random important data course work, music and movies HFS+ journaling off

3) About 60GB empty for linux EXT3

4) Empty FAT32 10GB

Once I started to copy large file >1GB onto EXT3 in Mac OS (i did install that random application for write support to ext2/3 I believe) and i realised i dragged onto wrong partition (wanted it on second). I clicked cancel on the copy function.

It canceled and straight away all partitions where ejected instantly and warning appeared that device was incorrectly removed. But USB was plugged in and I didn't touch it.

Since then my external hard drive doesn't mount anywhere. In Mac OS it appears in the system profiler under usb devices.

In Ubuntu GParted doesn't see it fdisk -l doesn't show it up but this is another output from terminal

```
dmitrij@dmitrij-laptop:~$ dmesg | tail
[  429.796000] scsi4 : SCSI emulation for USB Mass Storage devices
[  429.796000] usb-storage: device found at 7
[  429.796000] usbcore: registered new interface driver usb-storage
[  429.796000] usb-storage: waiting for device to settle before scanning
[  429.796000] USB Mass Storage support registered.
[  434.796000] usb-storage: device scan complete
[  434.796000] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  434.796000] sd 4:0:0:0: Attached scsi disk sdb
[  434.796000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  467.900000] applesmc: wait status failed: c != 18

dmitrij@dmitrij-laptop:/dev$ ls
acpi       ptyd4  ptysd  ptyy6       tty29  ttycf  ttys4  ttyxd
adsp       ptyd5  ptyse  ptyy7       tty3   ttyd0  ttys5  ttyxe
agpgart    ptyd6  ptysf  ptyy8       tty30  ttyd1  ttys6  ttyxf
audio      ptyd7  ptyt0  ptyy9       tty31  ttyd2  ttys7  ttyy0
bus        ptyd8  ptyt1  ptyya       tty32  ttyd3  ttys8  ttyy1
cdrom      ptyd9  ptyt2  ptyyb       tty33  ttyd4  ttys9  ttyy2
cdrw       ptyda  ptyt3  ptyyc       tty34  ttyd5  ttysa  ttyy3
console    ptydb  ptyt4  ptyyd       tty35  ttyd6  ttysb  ttyy4
core       ptydc  ptyt5  ptyye       tty36  ttyd7  ttysc  ttyy5
disk       ptydd  ptyt6  ptyyf       tty37  ttyd8  ttysd  ttyy6
dri        ptyde  ptyt7  ptyz0       tty38  ttyd9  ttyse  ttyy7
dsp        ptydf  ptyt8  ptyz1       tty39  ttyda  ttysf  ttyy8
dvd        ptye0  ptyt9  ptyz2       tty4   ttydb  ttyt0  ttyy9
dvdrw      ptye1  ptyta  ptyz3       tty40  ttydc  ttyt1  ttyya
fd         ptye2  ptytb  ptyz4       tty41  ttydd  ttyt2  ttyyb
full       ptye3  ptytc  ptyz5       tty42  ttyde  ttyt3  ttyyc
fuse       ptye4  ptytd  ptyz6       tty43  ttydf  ttyt4  ttyyd
hpet       ptye5  ptyte  ptyz7       tty44  ttye0  ttyt5  ttyye
initctl    ptye6  ptytf  ptyz8       tty45  ttye1  ttyt6  ttyyf
input      ptye7  ptyu0  ptyz9       tty46  ttye2  ttyt7  ttyz0
kmem       ptye8  ptyu1  ptyza       tty47  ttye3  ttyt8  ttyz1
kmsg       ptye9  ptyu2  ptyzb       tty48  ttye4  ttyt9  ttyz2
log        ptyea  ptyu3  ptyzc       tty49  ttye5  ttyta  ttyz3
loop0      ptyeb  ptyu4  ptyzd       tty5   ttye6  ttytb  ttyz4
MAKEDEV    ptyec  ptyu5  ptyze       tty50  ttye7  ttytc  ttyz5
mem        ptyed  ptyu6  ptyzf       tty51  ttye8  ttytd  ttyz6
mixer      ptyee  ptyu7  ram0        tty52  ttye9  ttyte  ttyz7
net        ptyef  ptyu8  ram1        tty53  ttyea  ttytf  ttyz8
null       ptyp0  ptyu9  ram10       tty54  ttyeb  ttyu0  ttyz9
nvidia0    ptyp1  ptyua  ram11       tty55  ttyec  ttyu1  ttyza
nvidiactl  ptyp2  ptyub  ram12       tty56  ttyed  ttyu2  ttyzb
oldmem     ptyp3  ptyuc  ram13       tty57  ttyee  ttyu3  ttyzc
port       ptyp4  ptyud  ram14       tty58  ttyef  ttyu4  ttyzd
ppp        ptyp5  ptyue  ram15       tty59  ttyp0  ttyu5  ttyze
psaux      ptyp6  ptyuf  ram2        tty6   ttyp1  ttyu6  ttyzf
ptmx       ptyp7  ptyv0  ram3        tty60  ttyp2  ttyu7  urandom
pts        ptyp8  ptyv1  ram4        tty61  ttyp3  ttyu8  usbdev1.1_ep00
ptya0      ptyp9  ptyv2  ram5        tty62  ttyp4  ttyu9  usbdev1.1_ep81
ptya1      ptypa  ptyv3  ram6        tty63  ttyp5  ttyua  usbdev1.4_ep00
ptya2      ptypb  ptyv4  ram7        tty7   ttyp6  ttyub  usbdev1.4_ep81
ptya3      ptypc  ptyv5  ram8        tty8   ttyp7  ttyuc  usbdev1.4_ep83
ptya4      ptypd  ptyv6  ram9        tty9   ttyp8  ttyud  usbdev1.4_ep84
ptya5      ptype  ptyv7  random      ttya0  ttyp9  ttyue  usbdev2.1_ep00
ptya6      ptypf  ptyv8  rtc         ttya1  ttypa  ttyuf  usbdev2.1_ep81
ptya7      ptyq0  ptyv9  scd0        ttya2  ttypb  ttyv0  usbdev3.1_ep00
ptya8      ptyq1  ptyva  sda         ttya3  ttypc  ttyv1  usbdev3.1_ep81
ptya9      ptyq2  ptyvb  sda1        ttya4  ttypd  ttyv2  usbdev3.2_ep00
ptyaa      ptyq3  ptyvc  sda2        ttya5  ttype  ttyv3  usbdev3.2_ep83
ptyab      ptyq4  ptyvd  sda3        ttya6  ttypf  ttyv4  usbdev4.1_ep00
ptyac      ptyq5  ptyve  sda4        ttya7  ttyq0  ttyv5  usbdev4.1_ep81
ptyad      ptyq6  ptyvf  sda5        ttya8  ttyq1  ttyv6  usbdev4.3_ep00
ptyae      ptyq7  ptyw0  sdb         ttya9  ttyq2  ttyv7  usbdev4.3_ep02
ptyaf      ptyq8  ptyw1  sequencer   ttyaa  ttyq3  ttyv8  usbdev4.3_ep03
ptyb0      ptyq9  ptyw2  sequencer2  ttyab  ttyq4  ttyv9  usbdev4.3_ep81
ptyb1      ptyqa  ptyw3  sg0         ttyac  ttyq5  ttyva  usbdev4.3_ep82
ptyb2      ptyqb  ptyw4  sg1         ttyad  ttyq6  ttyvb  usbdev4.3_ep83
ptyb3      ptyqc  ptyw5  sg2         ttyae  ttyq7  ttyvc  usbdev5.1_ep00
ptyb4      ptyqd  ptyw6  shm         ttyaf  ttyq8  ttyvd  usbdev5.1_ep81
ptyb5      ptyqe  ptyw7  snapshot    ttyb0  ttyq9  ttyve  usbdev5.3_ep00
ptyb6      ptyqf  ptyw8  snd         ttyb1  ttyqa  ttyvf  usbdev5.7_ep00
ptyb7      ptyr0  ptyw9  sndstat     ttyb2  ttyqb  ttyw0  usbdev5.7_ep02
ptyb8      ptyr1  ptywa  sr0         ttyb3  ttyqc  ttyw1  usbdev5.7_ep81
ptyb9      ptyr2  ptywb  stderr      ttyb4  ttyqd  ttyw2  vcs
ptyba      ptyr3  ptywc  stdin       ttyb5  ttyqe  ttyw3  vcs1
ptybb      ptyr4  ptywd  stdout      ttyb6  ttyqf  ttyw4  vcs2
ptybc      ptyr5  ptywe  tpm0        ttyb7  ttyr0  ttyw5  vcs3
ptybd      ptyr6  ptywf  tty         ttyb8  ttyr1  ttyw6  vcs4
ptybe      ptyr7  ptyx0  tty0        ttyb9  ttyr2  ttyw7  vcs5
ptybf      ptyr8  ptyx1  tty1        ttyba  ttyr3  ttyw8  vcs6
ptyc0      ptyr9  ptyx2  tty10       ttybb  ttyr4  ttyw9  vcs7
ptyc1      ptyra  ptyx3  tty11       ttybc  ttyr5  ttywa  vcs8
ptyc2      ptyrb  ptyx4  tty12       ttybd  ttyr6  ttywb  vcsa
ptyc3      ptyrc  ptyx5  tty13       ttybe  ttyr7  ttywc  vcsa1
ptyc4      ptyrd  ptyx6  tty14       ttybf  ttyr8  ttywd  vcsa2
ptyc5      ptyre  ptyx7  tty15       ttyc0  ttyr9  ttywe  vcsa3
ptyc6      ptyrf  ptyx8  tty16       ttyc1  ttyra  ttywf  vcsa4
ptyc7      ptys0  ptyx9  tty17       ttyc2  ttyrb  ttyx0  vcsa5
ptyc8      ptys1  ptyxa  tty18       ttyc3  ttyrc  ttyx1  vcsa6
ptyc9      ptys2  ptyxb  tty19       ttyc4  ttyrd  ttyx2  vcsa7
ptyca      ptys3  ptyxc  tty2        ttyc5  ttyre  ttyx3  vcsa8
ptycb      ptys4  ptyxd  tty20       ttyc6  ttyrf  ttyx4  watchdog
ptycc      ptys5  ptyxe  tty21       ttyc7  ttys0  ttyx5  xconsole
ptycd      ptys6  ptyxf  tty22       ttyc8  ttyS0  ttyx6  zero
ptyce      ptys7  ptyy0  tty23       ttyc9  ttys1  ttyx7
ptycf      ptys8  ptyy1  tty24       ttyca  ttyS1  ttyx8
ptyd0      ptys9  ptyy2  tty25       ttycb  ttys2  ttyx9
ptyd1      ptysa  ptyy3  tty26       ttycc  ttyS2  ttyxa
ptyd2      ptysb  ptyy4  tty27       ttycd  ttys3  ttyxb
ptyd3      ptysc  ptyy5  tty28       ttyce  ttyS3  ttyxc
```

Will I be able somehow get to the files on the second partition, please? (Any OS available, ready even to buy software although believe open-source can help better in this case)

---

### Post by ajtudor on 2007-10-19
It seems as if the partition table has been wiped.  The data should still be there, though.  I would try TestDisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck.

---

