---
title: "[SOLVED] Wheres My Windows Partition?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by larry wales on 2008-04-19
I Upgraded To 7.10 And Can't Find My Windows Partition Anymore.  It Used To Be In Dev/sda1 And Now Its Gone.  Where It Go?

---

### Post by adult swim on 2008-04-19
in a terminal run ```
sudo fdisk -l
``` and post the results

---

### Post by larry wales on 2008-04-19
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd202c021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        7235    19045057+  83  Linux
/dev/sda3            7236        7296      489982+  82  Linux swap / Solaris

```

---

### Post by adult swim on 2008-04-19
it is still there at /dev/sda1

---

### Post by larry wales on 2008-04-20
ITS LISTED BUT  I CAN'T ACCESS IT:

```
larry@larryscomputer:~$ cd /dev
troy@svatopluk:/dev$ ls
adsp       ptyce  ptys5  ptyxc       tty21  ttyc5  ttyrc   ttywe
agpgart    ptycf  ptys6  ptyxd       tty22  ttyc6  ttyrd   ttywf
audio      ptyd0  ptys7  ptyxe       tty23  ttyc7  ttyre   ttyx0
audio1     ptyd1  ptys8  ptyxf       tty24  ttyc8  ttyrf   ttyx1
bus        ptyd2  ptys9  ptyy0       tty25  ttyc9  ttys0   ttyx2
cdrom      ptyd3  ptysa  ptyy1       tty26  ttyca  ttyS0   ttyx3
cdrw       ptyd4  ptysb  ptyy2       tty27  ttycb  ttys1   ttyx4
console    ptyd5  ptysc  ptyy3       tty28  ttycc  ttyS1   ttyx5
core       ptyd6  ptysd  ptyy4       tty29  ttycd  ttys2   ttyx6
disk       ptyd7  ptyse  ptyy5       tty3   ttyce  ttyS2   ttyx7
dsp        ptyd8  ptysf  ptyy6       tty30  ttycf  ttys3   ttyx8
dsp1       ptyd9  ptyt0  ptyy7       tty31  ttyd0  ttyS3   ttyx9
dvd        ptyda  ptyt1  ptyy8       tty32  ttyd1  ttys4   ttyxa
dvdrw      ptydb  ptyt2  ptyy9       tty33  ttyd2  ttys5   ttyxb
fd         ptydc  ptyt3  ptyya       tty34  ttyd3  ttys6   ttyxc
full       ptydd  ptyt4  ptyyb       tty35  ttyd4  ttys7   ttyxd
fuse       ptyde  ptyt5  ptyyc       tty36  ttyd5  ttys8   ttyxe
hpet       ptydf  ptyt6  ptyyd       tty37  ttyd6  ttys9   ttyxf
initctl    ptye0  ptyt7  ptyye       tty38  ttyd7  ttysa   ttyy0
input      ptye1  ptyt8  ptyyf       tty39  ttyd8  ttysb   ttyy1
kmem       ptye2  ptyt9  ptyz0       tty4   ttyd9  ttysc   ttyy2
kmsg       ptye3  ptyta  ptyz1       tty40  ttyda  ttysd   ttyy3
log        ptye4  ptytb  ptyz2       tty41  ttydb  ttyse   ttyy4
loop0      ptye5  ptytc  ptyz3       tty42  ttydc  ttysf   ttyy5
lp0        ptye6  ptytd  ptyz4       tty43  ttydd  ttySL0  ttyy6
MAKEDEV    ptye7  ptyte  ptyz5       tty44  ttyde  ttyt0   ttyy7
mem        ptye8  ptytf  ptyz6       tty45  ttydf  ttyt1   ttyy8
mixer      ptye9  ptyu0  ptyz7       tty46  ttye0  ttyt2   ttyy9
mixer1     ptyea  ptyu1  ptyz8       tty47  ttye1  ttyt3   ttyya
modem      ptyeb  ptyu2  ptyz9       tty48  ttye2  ttyt4   ttyyb
net        ptyec  ptyu3  ptyza       tty49  ttye3  ttyt5   ttyyc
null       ptyed  ptyu4  ptyzb       tty5   ttye4  ttyt6   ttyyd
nvidia0    ptyee  ptyu5  ptyzc       tty50  ttye5  ttyt7   ttyye
nvidiactl  ptyef  ptyu6  ptyzd       tty51  ttye6  ttyt8   ttyyf
oldmem     ptyp0  ptyu7  ptyze       tty52  ttye7  ttyt9   ttyz0
parport0   ptyp1  ptyu8  ptyzf       tty53  ttye8  ttyta   ttyz1
port       ptyp2  ptyu9  ram0        tty54  ttye9  ttytb   ttyz2
ppp        ptyp3  ptyua  ram1        tty55  ttyea  ttytc   ttyz3
psaux      ptyp4  ptyub  ram10       tty56  ttyeb  ttytd   ttyz4
ptmx       ptyp5  ptyuc  ram11       tty57  ttyec  ttyte   ttyz5
pts        ptyp6  ptyud  ram12       tty58  ttyed  ttytf   ttyz6
ptya0      ptyp7  ptyue  ram13       tty59  ttyee  ttyu0   ttyz7
ptya1      ptyp8  ptyuf  ram14       tty6   ttyef  ttyu1   ttyz8
ptya2      ptyp9  ptyv0  ram15       tty60  ttyp0  ttyu2   ttyz9
ptya3      ptypa  ptyv1  ram2        tty61  ttyp1  ttyu3   ttyza
ptya4      ptypb  ptyv2  ram3        tty62  ttyp2  ttyu4   ttyzb
ptya5      ptypc  ptyv3  ram4        tty63  ttyp3  ttyu5   ttyzc
ptya6      ptypd  ptyv4  ram5        tty7   ttyp4  ttyu6   ttyzd
ptya7      ptype  ptyv5  ram6        tty8   ttyp5  ttyu7   ttyze
ptya8      ptypf  ptyv6  ram7        tty9   ttyp6  ttyu8   ttyzf
ptya9      ptyq0  ptyv7  ram8        ttya0  ttyp7  ttyu9   urandom
ptyaa      ptyq1  ptyv8  ram9        ttya1  ttyp8  ttyua   usb1
ptyab      ptyq2  ptyv9  random      ttya2  ttyp9  ttyub   usb2
ptyac      ptyq3  ptyva  rtc         ttya3  ttypa  ttyuc   usb3
ptyad      ptyq4  ptyvb  scd0        ttya4  ttypb  ttyud   usbdev1.1_ep00
ptyae      ptyq5  ptyvc  sda         ttya5  ttypc  ttyue   usbdev1.1_ep81
ptyaf      ptyq6  ptyvd  sda1        ttya6  ttypd  ttyuf   usbdev2.1_ep00
ptyb0      ptyq7  ptyve  sda2        ttya7  ttype  ttyv0   usbdev2.1_ep81
ptyb1      ptyq8  ptyvf  sda3        ttya8  ttypf  ttyv1   usbdev3.1_ep00
ptyb2      ptyq9  ptyw0  sequencer   ttya9  ttyq0  ttyv2   usbdev3.1_ep81
ptyb3      ptyqa  ptyw1  sequencer2  ttyaa  ttyq1  ttyv3   vcs
ptyb4      ptyqb  ptyw2  sg0         ttyab  ttyq2  ttyv4   vcs1
ptyb5      ptyqc  ptyw3  sg1         ttyac  ttyq3  ttyv5   vcs2
ptyb6      ptyqd  ptyw4  shm         ttyad  ttyq4  ttyv6   vcs3
ptyb7      ptyqe  ptyw5  snapshot    ttyae  ttyq5  ttyv7   vcs4
ptyb8      ptyqf  ptyw6  snd         ttyaf  ttyq6  ttyv8   vcs5
ptyb9      ptyr0  ptyw7  sndstat     ttyb0  ttyq7  ttyv9   vcs6
ptyba      ptyr1  ptyw8  sr0         ttyb1  ttyq8  ttyva   vcs7
ptybb      ptyr2  ptyw9  stderr      ttyb2  ttyq9  ttyvb   vcs8
ptybc      ptyr3  ptywa  stdin       ttyb3  ttyqa  ttyvc   vcsa
ptybd      ptyr4  ptywb  stdout      ttyb4  ttyqb  ttyvd   vcsa1
ptybe      ptyr5  ptywc  toshiba     ttyb5  ttyqc  ttyve   vcsa2
ptybf      ptyr6  ptywd  tty         ttyb6  ttyqd  ttyvf   vcsa3
ptyc0      ptyr7  ptywe  tty0        ttyb7  ttyqe  ttyw0   vcsa4
ptyc1      ptyr8  ptywf  tty1        ttyb8  ttyqf  ttyw1   vcsa5
ptyc2      ptyr9  ptyx0  tty10       ttyb9  ttyr0  ttyw2   vcsa6
ptyc3      ptyra  ptyx1  tty11       ttyba  ttyr1  ttyw3   vcsa7
ptyc4      ptyrb  ptyx2  tty12       ttybb  ttyr2  ttyw4   vcsa8
ptyc5      ptyrc  ptyx3  tty13       ttybc  ttyr3  ttyw5   watchdog
ptyc6      ptyrd  ptyx4  tty14       ttybd  ttyr4  ttyw6   xconsole
ptyc7      ptyre  ptyx5  tty15       ttybe  ttyr5  ttyw7   zero
ptyc8      ptyrf  ptyx6  tty16       ttybf  ttyr6  ttyw8
ptyc9      ptys0  ptyx7  tty17       ttyc0  ttyr7  ttyw9
ptyca      ptys1  ptyx8  tty18       ttyc1  ttyr8  ttywa
ptycb      ptys2  ptyx9  tty19       ttyc2  ttyr9  ttywb
ptycc      ptys3  ptyxa  tty2        ttyc3  ttyra  ttywc
ptycd      ptys4  ptyxb  tty20       ttyc4  ttyrb  ttywd
larry@larryscomputer:/dev$ cd sda1
bash: cd: sda1: Not a directory
larry@larryscomputer:/dev$

```

TIME IS RUNNING OUT - HOW CAN I GAIN ACCESS ADULT SWIM?

---

### Post by Jesuses Left Leg on 2008-04-20
You will have to mount it by
```
sudo mount /dev/sda1
```

It should then pop up on your desktop and in your file browser.
Alternatively you could try double clicking it in nautilus if it is there to mount it.

If this doesnt work post the output of ```
cat /etc/fstab
```.

/dev/sda1 is not accessible as a folder, which is why you need to mount it so you can access it first.

---

### Post by larry wales on 2008-04-21
I TRIED TO MOUNT, GOT THIS REPLY:

```
fuse: mount failed: Device or resource busy
```

NO LUCK DOUBLE-CLICKING IN NAUTILUS.

HERES cat /etc/fstab OUTPUT:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0410006310005DD4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a0fbbd66-7e52-4442-9deb-c365e6e6d5a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by natirips on 2008-04-21
Have you tried to go to /media/sda1 ?

---

### Post by Oldsoldier2003 on 2008-04-21
> **larry wales said:**
> I TRIED TO MOUNT, GOT THIS REPLY:

```
fuse: mount failed: Device or resource busy
```

NO LUCK DOUBLE-CLICKING IN NAUTILUS.

HERES cat /etc/fstab OUTPUT:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0410006310005DD4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a0fbbd66-7e52-4442-9deb-c365e6e6d5a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

boot into windows and run chkdsk. you probably had a dirty shutdown and ubuntu will not mount the NTFS filesystem  unless the dirty bit has been cleared or you use the force option. Its always better to run chkdsk unless you dont have a Windows installation, in which case you can force the mount using 
```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force
```

---

### Post by MakotoTheKnight on 2008-04-21
Alright, try this:

1.  Run the command sudo umount /dev/sda1
2.  Run the command sudo mount /dev/sda1 /media/DISK/

It could be that you also need ntfs-3g, not too sure at this point, but for now I'd do without it, just in case.

Let us know how it goes.

---

### Post by Oldsoldier2003 on 2008-04-21
> **MakotoTheKnight said:**
> Alright, try this:

1.  Run the command sudo umount /dev/sda1
2.  Run the command sudo mount /dev/sda1 /media/DISK/

It could be that you also need ntfs-3g, not too sure at this point, but for now I'd do without it, just in case.

Let us know how it goes.

ntfs-3g is part of gutsy by default IIRC, but having already tried to mount the partition i'm pretty much betting its a issue of a dirty shutdown of the NTFS filesystem.

---

### Post by natirips on 2008-04-21
> **larry wales said:**
> ...
HERES cat /etc/fstab OUTPUT:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bc0531d2-f92f-41df-90c1-14cc3487c560 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0410006310005DD4 [SIZE="7"]/media/sda1[/SIZE]     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a0fbbd66-7e52-4442-9deb-c365e6e6d5a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Someone correct me if I'm wrong/retarded, but it's already mounted in /media/sda1. :)

---

### Post by larry wales on 2008-04-21
OK, WHEN I GO TO /media/sda1 IN NAUTILUS THE sda1 FOLDER EXISTS BUT IT IS EMPTY.  

FROM CMDLINE:

```
larry@larryscomputer:/media$ ls
cdrom  cdrom0  sda1
larry@larryscomputer:/media$ cd sda1
larry@larryscomputer:/media/sda1$ ls
larry@larryscomputer:/media/sda1$ 

```


 
THEN TRIED THIS:

```
larry@larryscomputer:/media$ sudo umount /dev/sda1
larry@larryscomputer:/media$ sudo mount /dev/sda1 /media/DISK/
fuse: failed to access mountpoint /media/DISK/: No such file or directory

```

I ALSO MADE SURE ON 2 OCCASIONS THAT I SHUT DOWN WINDOWS GOOD AND PROPER BUT THIS HAD NO INFLUENCE.  CAN I FORCE THE MOUNT?  IF SO HOW?

---

### Post by Oldsoldier2003 on 2008-04-21
> **natirips said:**
> Someone correct me if I'm wrong/retarded, but it's already mounted in /media/sda1. :)

just because its in the fstab doesn't mean its mounted :)

---

### Post by hums07 on 2008-04-21
Try this
```
sudo mount /dev/sda1 /media/sda1
ls /media/sda1
```

If NTFS was not properly shutdown, there will be a message when you try to mount it.

---

### Post by Joeb454 on 2008-04-21
You could simply try installing ntfs-config, it'll provide a nice simple GUI for mounting NTFS drives.

Also please stop shouting (a.k.a typing IN CAPS), we can read lowercase too :)

---

### Post by natirips on 2008-04-21
Try changing the "DISK" part with "sda1".

---

### Post by ace007 on 2008-04-21
This problem is most commonly found in laptops when Windows is in Hibernate.  More than likely Windows was not shut down properly, because it appears that all of your settings are correct.  Boot to windows and properly shut it down to see if it relieves the problem.

---

### Post by bodhi.zazen on 2008-04-21
@ larry wales

hard drives are accessed from the mount point, not /dev/sda1

@ all, to see if a device is mounted, use the mount command :

```
mount
```

If the device is not mounted, mount it.

```
sudo mount /dev/sda1
```

If it is mounted and you can not access it, then we have a permissions problem

See this link or post additional information 

ie output of mount and ls -l /media

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by MongooseCage on 2008-04-21
Could Super Grub Disk or something find it? Noob suggestion.

---

### Post by larry wales on 2008-04-21
OKAY I DID THIS:

```
larry@larryscomputer:/media/sda1$ sudo mount /dev/sda1 /media/sda1
[sudo] password for larry:
larry@larryscomputer:/media/sda1$ ls /media/sda1
Activities              MSDOS.SYS                   T305
AUTOEXEC.BAT            MySQL                       tapestry-annotations
boot.ini                mysql-connector-java-5.0.4  tapestry-core
CanoScan                NOTICE.txt                  tapestry-hibernate
CONFIG.SYS              NTDETECT.COM                tapestry-ioc
Documents and Settings  ntldr                       tapestry-spring
GWTBook                 openrico                    tapestry-test
gwt-windows-1.4.61      OpenSSL                     tapestry-tutorial1
HG-CLONE                packs                       tapestry-upload
hiberfil.sys            pagefile.sys                TRANSLAT
hibernate-3.2           Program Files               wamp
IO.SYS                  RECYCLER                    WINDOWS
JBuilder4               SunIT
LICENSE-2.0.txt         System Volume Information

```

NOW THATS STARTING TO LOOK MORE LIKE IT!!

AND THEN I GO TO /media/sda1 IN NAUTILUS AND ALL MY STUFF IS THERE!!!!

THANKS hums07 FOR THE ADVISE YOUR AWESOME

AND Joeb454 I'M STILL SHOUTING BUT THESE ARE WORDS OF JOY!!:-D:-D:-D:-D:p

MAY THIS HAPPENED BECUZ MY WINDOWS WAS HIBERNATING AT THE TIME I DID THE UPGRADE TO GUTSY??

WE SHOULD ALL GET TOGETHER FOR A BEER

---

### Post by kansasnoob on 2008-04-21
I had the same problem upgrading from 7.10 to 8.04RC on a dual boot with win XP.

Warning though: I'm a total noob (hence the moniker) so I'd prefer you get some more opinions before proceeding.

Anyway it appears that the upgrade rewrote the GRUB menu file so I followed the "Modify the Boot Menu" section in this dual boot tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It worked for me, but be cautious following my advice, I've only been at this about 2 months and I've totally hosed a couple of installs and had to start over from scratch.

---

### Post by bodhi.zazen on 2008-04-21
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by larry wales on 2008-04-21
[CENTER]Marked As Solved 

\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/

Ok Bye!![/CENTER]

---

### Post by DBrocks on 2008-04-21
CAPS LOCK IS CRUISE-CONTROL FOR COOL!!!!
 
Just kidding :guitar:

---

