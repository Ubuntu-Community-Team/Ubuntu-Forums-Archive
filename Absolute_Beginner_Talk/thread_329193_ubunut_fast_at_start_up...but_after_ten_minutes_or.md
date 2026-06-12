---
title: "ubunut fast at start up...but after ten minutes or so......"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2007-01-01
it starts getting really slow, to the point where programs are taking ten plus seconds to do very small things, such as save or close.  its odd because at start up its running faster than windows was going before i switched over.  any ideers?

---

### Post by andrewpb on 2007-01-01
and yes i just saw that i wrote "ubunut" at least that typo is funny

---

### Post by obsidion on 2007-01-01
> **andrewpb said:**
> and yes i just saw that i wrote "ubunut" at least that typo is funny

  Have you installed something that has a memory leak, what does top tell you ?

---

### Post by andrewpb on 2007-01-01
what do you mean "top"?

---

### Post by taurus on 2007-01-01
What much RAM and swap space do you have?

Applications -> Accessories -> Terminal
```
free
```
p.s.  He meant type "**top**" from a terminal to see which process is eating up your memory.

---

### Post by andrewpb on 2007-01-01
this is what free spits out

             total       used       free     shared    buffers     cached
Mem:        515804     482188      33616          0        772     337060
-/+ buffers/cache:     144356     371448
Swap:      4184924          0    4184924


and top says that something with the command "xorg" is uding 27% of the cpu with firefox and it says there is 91 programs running??? with 90 sleeping??  as of now i only have firefox and two terminals open.

---

### Post by taurus on 2007-01-01
Looks like the system is not even touching your swap!  Does it get slow a few minutes after you boot up Ubuntu and stays slow for the duration of time (hours) when you use it?

It could be **updatedb** is slowing down your machine...

---

### Post by andrewpb on 2007-01-01
it does pretty much what you're explaining.  how could i make it at least touch the swap drive?

---

### Post by taurus on 2007-01-01
It will use your swap partition when it needs to.  You want it to use your RAM since RAM is much faster than swap.  However, does your machine continue to be slow after updatedb finished?  Updatedb usually takes a few minutes for it to finish because you can see the red light on your harddrive flashing (or hear your harddrive working hard).

---

### Post by andrewpb on 2007-01-01
is updatedb the program that looks for updates and let's me know there is an update on the top right corner of my screen?

---

### Post by steve.horsley on 2007-01-01
It won't use swap unless it needs more memory that it physically has. So you can only "make it" use swap by starting lots more programs. 

It may be worth putting the system monitor widget on the taskbar so you can see what's going on. Right-click one of the bars and choose Add To Panel... Then in System & Hardware, add System Monitor. Then you can right-click the icon on the panel and choose what to display - memory, swap and CPU are probably the ones you are interested in. This should give you a feel for what's slowing things down.

I think updatedb indexes the filesystem so that the **locate** command can tell you where files are real quick.

---

### Post by taurus on 2007-01-01
Actually, updatedb is the database for slocate command.  

```
man updatedb
```

---

### Post by andrewpb on 2007-01-01
so i did that command and i pressed enter through the lines and nothing seems to be happening in terminal and this is what the last line reads

 Manual page updatedb(1) line 35/59 (END)


?

---

### Post by taurus on 2007-01-01
It's just a manpage for updatedb in case you want to read it so don't worry about it.  However, does your machine continue to be slow after updatedb finished running?

---

### Post by andrewpb on 2007-01-01
yup, just as slow, if not a little slower

---

### Post by taurus on 2007-01-01
I know you have 512MB of RAM but what's the spec of your machine?  And I assume you are running Edgy (Gnome)!

---

### Post by andrewpb on 2007-01-01
i'm running dapper (gnome) and when i partitioned i set aside 18 gigs for ubuntu and 4 gigs for a swap.

---

### Post by andrewpb on 2007-01-01
i should add that when i just posted my last comment i looked up at the system moniter (which has three small graphs at the top center of my screen) all three said the processor was running at 100%

---

### Post by taurus on 2007-01-01
When your CPU peaks at 100%, run the **top** command from a terminal again to see which process "spikes" your CPU!!!

Does this just happen recently or does it happen ever since you installed Dapper on your machine?

---

### Post by andrewpb on 2007-01-01
its been doing it since i installed dapper

and it says this is the thing at the top

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND

 4401 root      16   0 25536  18m 7196 R 48.0  3.6  24:32.25 Xorg

---

### Post by taurus on 2007-01-01
So xorg is keeping your machine busy!!!  What graphic card do you have and by any change you did install a driver for it?

Post the complete output of the top command here then.

```
top
```

---

### Post by andrewpb on 2007-01-01
this the complete output

top - 09:11:00 up  2:53,  2 users,  load average: 0.71, 0.43, 0.39
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 42.1% us,  8.6% sy,  0.0% ni, 49.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    515804k total,   494900k used,    20904k free,      772k buffers
Swap:  4184924k total,        0k used,  4184924k free,   345092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4401 root      16   0 25372  18m 7196 R 17.1  3.6  25:27.09 Xorg
 6340 everyone  15   0  156m  40m  19m S 10.5  8.0   8:41.43 firefox-bin
 4941 everyone  15   0 56908  18m  12m S  3.3  3.7   0:45.89 gnome-panel
 9427 everyone  15   0 70764  15m 9536 S  1.3  3.0   0:15.39 gnome-terminal
 9451 everyone  16   0  2196 1100  856 R  1.0  0.2   0:04.86 top
 4952 everyone  15   0 19072  10m 7672 S  0.3  2.0   0:03.31 update-notifier
 5016 everyone  15   0 14820 5164 3996 S  0.3  1.0   0:09.28 gnome-screensav
    1 root      16   0  1564  528  460 S  0.0  0.1   0:05.02 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.52 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
    9 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  138 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.46 pdflush


and i'm not sure what graphic card i have, it should just be what came with the system when i got it.  its a dell inspiron 5160

---

### Post by taurus on 2007-01-01
If it's a Dell, it's probably one of those Intel onboard graphic controller things!!!  Paste this output here to find out for sure.

```
lspci
```
Do inspirons use Celeron chips?

```
cat /proc/cpuinfo
```

---

### Post by andrewpb on 2007-01-01
for the first output you asked for...

0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: Trident Microsystems XGI Volari XP5 (rev 02)
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller


and the second...

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 1
cpu MHz         : 2791.375
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 5619.48


thanks!

---

### Post by taurus on 2007-01-01
Yip.  It's an Intel onboard graphic card alright.

0000:00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)

So, it's a P4 with 2.80MHz.  Should be a fast machine...  The problem could be in your harddrive which I assume it's a 4500RPM.  Wonder if you have DMA enable for your harddrive?

```
sudo hdparm -tT /dev/hda
```

---

### Post by andrewpb on 2007-01-01
and here is the output

read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error

---

### Post by taurus on 2007-01-01
What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by andrewpb on 2007-01-01
Disk /dev/hdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           8       64228+   b  W95 FAT32
/dev/hdc2   *           9        2048    16386300    7  HPFS/NTFS
/dev/hdc3            2570        4864    18434587+  83  Linux
/dev/hdc4            2049        2569     4184932+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2007-01-01
Okay, it's /dev/hdc then...

```
sudo hdparm -tT /dev/hdc
```
Just curious.  What does your /etc/fstab look like anyway?

```
cat /etc/fstab
```

---

### Post by andrewpb on 2007-01-01
first output

/dev/hdc:
 Timing cached reads:   240 MB in  2.56 seconds =  93.74 MB/sec
 Timing buffered disk reads:   50 MB in  3.05 seconds =  16.40 MB/sec

second output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               jfs     defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hdc2       /media/hdc2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdc4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-01-01
Try this to see if there is any improvement to your harddrive!

```
sudo hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hdc
sudo hdparm -tT /dev/hdc
```

---

### Post by andrewpb on 2007-01-01
first output

/dev/hdc:
 setting fs readahead to 64
 setting multcount to 16
 setting unmaskirq to 1 (on)
 setting using_dma to 1 (on)
 setting drive read-lookahead to 1 (on)
 multcount    = 16 (on)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 readahead    = 64 (on)
everyone@thelovemachine:~$ sudo hdparm -tT /dev/hdc

second output

 Timing cached reads:   260 MB in  2.77 seconds =  93.92 MB/sec
 Timing buffered disk reads:   76 MB in  3.22 seconds =  23.63 MB/sec

and as of now there is no improvement, i'll restart the computer in several minutes and see if that works

thanks so much for the help as always

---

### Post by andrewpb on 2007-01-01
i restarted the computer....and its still as slow as ever...garshed darned it all...any ideers?

---

### Post by taurus on 2007-01-01
If you don't have any important data on Dapper (make a backup if you do), perhaps you should consider reinstalling it from fresh BUT use **ext3** filesystem instead of jfs.  See if that speeds up harddrive!!!

---

### Post by andrewpb on 2007-01-01
i shall try that!

Thanks again

---

### Post by andrewpb on 2007-01-06
sigh, i finally got around to doing it, however...it is still slow...should i upgrade to edgy and see if that does anything?

---

### Post by andrewpb on 2007-01-07
anyone?

---

