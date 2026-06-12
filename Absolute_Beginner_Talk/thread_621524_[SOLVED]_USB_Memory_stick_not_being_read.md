---
title: "[SOLVED] USB Memory stick not being read"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-23
I have a 13-in-1 (or whatever) card reader on my Dell.  When I was on Feisty, it would detect my camera's memory stick as soon as I plugged it in, and automatically mount it in /media.

I am now using Gutsy, and it doesn't do squat when I insert the memory stick.

Here's the output of a few things, but I'm not which (if any) will be helpful:

```
sarteck@auron:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```
```
sarteck@auron:~$ lsusb
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0644:0200 TEAC Corp.
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp.
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd
Bus 002 Device 001: ID 0000:0000
```
```
sarteck@auron:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5cc0c4fc-35b8-42fd-89f3-0326c6d7e07b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=52DE9C11DE9BEB8B /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C8ACF90AACF8F3B2 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a3e2c99f-e26f-48b9-a9f8-03ecefa0619f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I've read that some people have had problems with their memory stick's being Read Only--I really don't care if it's Read Only, just as long as I can access it! XD

If it matters at all, the memory stick is a 32MB Sony something or other, and all the pictures taken with it are named "DSCnnnnn.jpg" (where "n" is a number--there might be six digits, not five, I can't remember for sure).

---

### Post by taurus on 2007-11-23
What about

```
sudo fdisk -l
```

---

### Post by Sarteck on 2007-11-23
Sorry, didn't know about taht one.  Heh.```
sarteck@auron:~$ sudo fdisk -l
[sudo] password for sarteck:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520    7  HPFS/NTFS
/dev/sda2            2611       54828   419430400    7  HPFS/NTFS
/dev/sda3           60552       60801     2008125   82  Linux swap / Solaris
/dev/sda4           54829       60551    45969997+  83  Linux

Partition table entries are not in disk order
```

---

### Post by Sarteck on 2007-11-23
As an additional note, it -does- get read when I boot into Windows.  So it's not a total loss, but that was the first time I had to boot into Windows for something in months, and it makes me sad. :(

---

### Post by Sarteck on 2007-11-24
An early-morning bump to see if any night-owls have a solution for me.

---

### Post by derby007 on 2007-11-24
I have a Dell with a card reader aswell but unfortunatley for u, I haven't used it yet! but......is the memory card for a Sony camera, if so, leave the card in the camera, and connect the camera to the PC via its mini USB cable to USB on the PC, I'm making presumptions here as I have a Sony camera & it works this way.........hope this helps.

---

### Post by Sarteck on 2007-11-24
The unfortunate bit there is that, unfortunately, the USB cord is (for all intents and purposes) unavailable--hence why I didn't mind paying the extra $20 to Dell to get me the card reader.  (Long story short, it's stuck in the house of my brother's ex-girlfriend.)

But that's not the only reason--I also got it for other cameras.  I semi-regularly used to use three of the four different slots there for the people around town bringing their photos in (I work at the local paper, see, and it helps to have something on hand that can quickly and easily download the photos).

It's no huge deal, seeing as how I can still accomplish it by booting into Windows.  However, as mentioned, I really don't like Windows anymore...  It almost seems foreign to me (something I never thought would happen).  It -did- work for sure in Feisty all the time...  just not in Gutsy.

---

### Post by derby007 on 2007-11-24
I'll see if mine works tonite, post back results later....

---

### Post by Sarteck on 2007-11-24
Well, I researched a bit more, and found yet another item I should include when asking the forum about an error I'm having:  the all-mighty "dmesg" and equally useful "tail".  Get this!  I even read the "man" files on both!  :O <--- (shock and surprise)

Anyways, **dmesg | tail -n 100** gave me output that I didn't like, but at least it might point somewhere in the general direction of where the problem may be.  (I won't include all 100 lines, but only from the point where I guess it's seeing my memory card.)

```
sarteck@auron:~$ dmesg | tail -n 100
[13564.497220] sd 2:0:0:2: [sdd] 63424 512-byte hardware sectors (32 MB)
[13564.505877] sd 2:0:0:2: [sdd] Write Protect is off
[13564.505879] sd 2:0:0:2: [sdd] Mode Sense: 87 00 00 00
[13564.505881] sd 2:0:0:2: [sdd] Assuming drive cache: write through
[13564.511009] sd 2:0:0:2: [sdd] 63424 512-byte hardware sectors (32 MB)
[13564.514759] sd 2:0:0:2: [sdd] Write Protect is off
[13564.514761] sd 2:0:0:2: [sdd] Mode Sense: 87 00 00 00
[13564.514763] sd 2:0:0:2: [sdd] Assuming drive cache: write through
[13564.514765]  sdd:end_request: I/O error, dev sdd, sector 0
[13564.525126] printk: 47 messages suppressed.
[13564.525129] Buffer I/O error on device sdd, logical block 0
[13564.526772] end_request: I/O error, dev sdd, sector 0
[13564.526775] Buffer I/O error on device sdd, logical block 0
[13564.528289] end_request: I/O error, dev sdd, sector 0
[13564.528292] Buffer I/O error on device sdd, logical block 0
[13564.529807] end_request: I/O error, dev sdd, sector 0
[13564.529810] Buffer I/O error on device sdd, logical block 0
[13564.531414] end_request: I/O error, dev sdd, sector 0
[13564.531417] Buffer I/O error on device sdd, logical block 0
[13564.522580] ldm_validate_partition_table(): Disk read failed.
[13564.532932] end_request: I/O error, dev sdd, sector 0
[13564.532934] Buffer I/O error on device sdd, logical block 0
[13564.534583] end_request: I/O error, dev sdd, sector 0
[13564.534586] Buffer I/O error on device sdd, logical block 0
[13564.536109] end_request: I/O error, dev sdd, sector 0
[13564.536111] Buffer I/O error on device sdd, logical block 0
[13564.537886] end_request: I/O error, dev sdd, sector 0
[13564.537889] Buffer I/O error on device sdd, logical block 0
[13564.529086] Dev sdd: unable to read RDB block 0
[13564.539449] end_request: I/O error, dev sdd, sector 0
[13564.539452] Buffer I/O error on device sdd, logical block 0
[13564.540966] end_request: I/O error, dev sdd, sector 0
[13564.542573] end_request: I/O error, dev sdd, sector 24
[13564.544091] end_request: I/O error, dev sdd, sector 24
[13564.545742] end_request: I/O error, dev sdd, sector 0
[13564.547304] end_request: I/O error, dev sdd, sector 0
[13564.538466]  unable to read partition table
[13564.551858] end_request: I/O error, dev sdd, sector 63232
[13564.553464] end_request: I/O error, dev sdd, sector 63232
[13564.554982] end_request: I/O error, dev sdd, sector 63408
[13564.556589] end_request: I/O error, dev sdd, sector 63408
[13564.558106] end_request: I/O error, dev sdd, sector 0
[13564.559623] end_request: I/O error, dev sdd, sector 0
[13564.561230] end_request: I/O error, dev sdd, sector 0
[13564.562748] end_request: I/O error, dev sdd, sector 63416
[13564.564355] end_request: I/O error, dev sdd, sector 63416
[13564.565873] end_request: I/O error, dev sdd, sector 63416
[13564.567525] end_request: I/O error, dev sdd, sector 63416
[13564.569042] end_request: I/O error, dev sdd, sector 63416
[13564.570560] end_request: I/O error, dev sdd, sector 63416
[13564.573211] end_request: I/O error, dev sdd, sector 63360
[13564.575380] end_request: I/O error, dev sdd, sector 63408
[13564.576897] end_request: I/O error, dev sdd, sector 63416
[13564.578505] end_request: I/O error, dev sdd, sector 63416
[13564.580022] end_request: I/O error, dev sdd, sector 0
[13564.581495] end_request: I/O error, dev sdd, sector 0
[13564.583146] end_request: I/O error, dev sdd, sector 0
[13564.584664] end_request: I/O error, dev sdd, sector 0
[13564.586271] end_request: I/O error, dev sdd, sector 0
[13564.587789] end_request: I/O error, dev sdd, sector 0
[13564.589306] end_request: I/O error, dev sdd, sector 0
[13564.590913] end_request: I/O error, dev sdd, sector 0
[13564.592431] end_request: I/O error, dev sdd, sector 0
[13564.594083] end_request: I/O error, dev sdd, sector 0
[13564.595600] end_request: I/O error, dev sdd, sector 0
[13564.597207] end_request: I/O error, dev sdd, sector 0
[13564.598724] end_request: I/O error, dev sdd, sector 0
[13564.600242] end_request: I/O error, dev sdd, sector 0
[13564.601849] end_request: I/O error, dev sdd, sector 0
[13564.603367] end_request: I/O error, dev sdd, sector 0
[13564.604973] end_request: I/O error, dev sdd, sector 0
[13564.606491] end_request: I/O error, dev sdd, sector 0
[13564.608098] end_request: I/O error, dev sdd, sector 0
[13564.609616] end_request: I/O error, dev sdd, sector 0
[13564.611133] end_request: I/O error, dev sdd, sector 0
[13564.612741] end_request: I/O error, dev sdd, sector 0
[13564.614258] end_request: I/O error, dev sdd, sector 0
[13564.615909] end_request: I/O error, dev sdd, sector 0
[13564.617382] end_request: I/O error, dev sdd, sector 0

```

Note:  The first line IS picking up on my memory stick!  32MB!  Yay!

'Course, the I/O errors following kind of put a damper on that "yay."

---

### Post by Sarteck on 2007-11-24
Bump for the mornign crew, who may hopefully be able to help.  :)

---

### Post by philinux on 2007-11-24
Put the card in and then fire up the app gthumb from graphics menu. Its pretty good at waking up phones cameras etc.

---

### Post by philinux on 2007-11-24
Put the card in and then fire up the app gthumb from graphics menu. Its pretty good at waking up phones cameras etc. Also if its on a hub try connecting directly.

---

### Post by Sarteck on 2007-11-24
philinux:  I had to install gthumb, but it didn't really do anything.  :/




Thread:  I installed "lsscsi" and...```
sarteck@auron:~$ lsscsi
[0:0:0:0]    disk    ATA      ST3500630AS      3.AD  /dev/sda
[1:0:0:0]    cd/dvd  TSSTcorp DVD+-RW TS-H653A D500  /dev/scd0
[2:0:0:0]    disk    TEAC     USB   HS-CF Card 4.00  /dev/sdb
[2:0:0:1]    disk    TEAC     USB   HS-xD/SM   4.00  /dev/sdc
[2:0:0:2]    disk    TEAC     USB   HS-MS Card 4.00  /dev/sdd
[2:0:0:3]    disk    TEAC     USB   HS-SD Card 4.00  /dev/sde
```Not sure if that help any with the problem, though.

[EDIT]P.S., Oh yeah, it would be the /dev/sdd that's being a bitch at the moment, but I have no way of testing sdb,sdc,or sde.

---

### Post by philinux on 2007-11-24
as Taurus asked whats the output of

 ```
[FONT="Times New Roman"]sudo fdisk -l[/FONT]
```

---

### Post by Sarteck on 2007-11-24
Thought I answered that...  Ah, well, here it is in case I didn't:```
sarteck@auron:~$ sudo fdisk -l
[sudo] password for sarteck:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520    7  HPFS/NTFS
/dev/sda2            2611       54828   419430400    7  HPFS/NTFS
/dev/sda3           60552       60801     2008125   82  Linux swap / Solaris
/dev/sda4           54829       60551    45969997+  83  Linux

Partition table entries are not in disk order
```

---

### Post by philinux on 2007-11-24
Ah yes sorry,

With the card in try ```
sudo mount /dev/sdd
```

Or whatever sudo is in kubuntu

---

### Post by Sarteck on 2007-11-24
sudo is still sudo in Kubuntu.  :)  It's just a different GUI--we both have the same backend.  (Therefore, I can't say anyone is a bigger butthole than me, I suppose.  XD)

```
sarteck@auron:~$ sudo mount /dev/sdd
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
```

I was Googling and found similar problems--similar, but not the same--that suggested something about the kernel.  I wasn't too sure, though, since the card was being read just fine when I was on Feisty Fawn, but is not being read all that well now that I'm on Gutsy.

---

### Post by philinux on 2007-11-24
did you click the link in my sig - try it.

---

### Post by Sarteck on 2007-11-24
philinux!  You're a genius!

It took a littoe link-hopping to do it, but I finally managed upon a post telling me what to do.  It was so simple, too:```
sudo apt-get install usbmount
```**NOTE:** For those of you having this same problem, I -did- have to reboot my system before it took effect.  **ALSO NOTE:** Just before I tried this, I also read a post about downgrading to the Feisty version of HAL, and did so.  It's possible that is what caused it to work--I don't really know.  I would assume it's the usbmount, though.  Or maybe a combination of the two.

---

### Post by derby007 on 2007-11-24
Change your Title to [Solved] pls. It may help others.

---

### Post by Sarteck on 2007-11-24
Was already doing that. ;)  Give mah slow connection a chance for me to load the edit screen.  XD

---

### Post by philinux on 2007-11-24
> **Sarteck said:**
> philinux!  You're a genius!

.

Glad to help.

---

### Post by derby007 on 2007-11-24
OK I'll let u off this time.
PS. I feel like the school master, now go and do 500 laps of the school yard......running backwards ........on one foot.... :)

---

