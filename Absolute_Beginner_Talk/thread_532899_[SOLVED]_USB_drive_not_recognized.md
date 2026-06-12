---
title: "[SOLVED] USB drive not recognized"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by koosfoto.hu on 2007-08-23
Greetings,

I am using Ubuntu or Kubuntu on my PC. I have an USB pen-drivewhat I insert often. Since a while my system has difficulties to recognize it. If and when I restarted Kubuntu or I changed to Ubuntu, it, however, worked. 
Today I have tried all the tricks... and nothing. 
The little light is lit on the USB pen, bu my system seems to know nothing about it.
I have read through the messages in the forum... and most of the things I do not understand.

I am a simple user (a photographer), and I have my work on the drive.
Could someone, please, tell me, what and how to do?
Please, keep it simple, so I can follow...

Thanks,


Tamas

---

### Post by Dr Small on 2007-08-23
First off, what exactly is it doing?
Is it giving an error, or just not doing anything?

---

### Post by koosfoto.hu on 2007-08-23
Hi Dr Small!

It is nice to have you here so quickly!

Well, there is NO message, nothing on the scren!
I plug it in or out... my system "does not care"... No message whatsoever.

Thanks,


Tamas

---

### Post by Dr Small on 2007-08-23
I have a USB Flash drive that does about the same thing. I think mine is about finished...
Perhaps you could use a new one too?

That looks like the only plausible reasoning, otherwise you would receive some sort of error. Lots of times, I'll plug mine in, and it won't do anything, then other times it will work perfectly. It's a sign of a bad USB.

I need a new one anyways...
Dr Small

---

### Post by koosfoto.hu on 2007-08-23
Well, mine is working perfectly well... in OTHER computers, in Windows!
So, I do not think, that my case is your case.

Anyhow, good luck to buy a new one!
:-)

Tamas

---

### Post by Terl on 2007-08-23
Just curious, have you tried to access it when it is plugged in whether the system recognizes it or not?

---

### Post by koosfoto.hu on 2007-08-23
Hi Terl!

HOW can I access it, if it is not seen on my desktop?
WHERE can I find it elsewhere??????

So, I did not try to access it... :-(

Greetings,

Tamas

---

### Post by schorsch on 2007-08-23
After plugging the device in open a terminal (Applicatons--> Accessories --> Terminal) and type the following commands:
```

mount
dmesg | tail -50
```
and post the output here.

---

### Post by ajgreeny on 2007-08-23
You should also have a look in your file manager in the /media folder.  There may be an entry for the drive there, but for some reason it is not appearing on the desktop as an icon.

---

### Post by koosfoto.hu on 2007-08-23
Hi ajgreeny,

Here it is... (I do not understand it, at all...(

woxom@Yellorange:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
woxom@Yellorange:~$ dmesg | tail -50
[ 4525.508000] scsi 3:0:0:0: rejecting I/O to dead device
[ 4525.508000]  unknown partition table
[ 4540.724000] Inbound IN=ppp0 OUT= MAC= SRC=213.238.121.234 DST=213.178.117.53 LEN=64 TOS=0x00 PREC=0x00 TTL=36 ID=11447 DF PROTO=TCP SPT=2990 DPT=2967 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4542.112000] usb 2-2: new full speed USB device using uhci_hcd and address 6
[ 4542.256000] usb 2-2: not running at top speed; connect to a high speed hub
[ 4542.276000] usb 2-2: configuration #1 chosen from 1 choice
[ 4542.280000] hub 2-2:1.0: USB hub found
[ 4542.284000] hub 2-2:1.0: 4 ports detected
[ 4546.128000] usb 2-2.3: new full speed USB device using uhci_hcd and address 7
[ 4546.228000] usb 2-2.3: not running at top speed; connect to a high speed hub
[ 4546.256000] usb 2-2.3: configuration #1 chosen from 1 choice
[ 4546.260000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4546.260000] usb-storage: device found at 7
[ 4546.260000] usb-storage: waiting for device to settle before scanning
[ 4551.260000] usb-storage: device scan complete
[ 4551.264000] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[ 4552.588000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[ 4552.592000] sdb: Write Protect is off
[ 4552.592000] sdb: Mode Sense: 03 00 00 00
[ 4552.592000] sdb: assuming drive cache: write through
[ 4552.604000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[ 4552.612000] sdb: Write Protect is off
[ 4552.612000] sdb: Mode Sense: 03 00 00 00
[ 4552.612000] sdb: assuming drive cache: write through
[ 4552.612000]  sdb:<6>usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4555.596000] usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4557.804000] usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4559.236000] end_request: I/O error, dev sdb, sector 0
[ 4559.236000] printk: 13 messages suppressed.
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] ldm_validate_partition_table(): Disk read failed.
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Dev sdb: unable to read RDB block 0
[ 4559.236000]  unknown partition table
[ 4559.236000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 4559.236000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 4571.868000] Inbound IN=ppp0 OUT= MAC= SRC=200.41.120.219 DST=213.178.117.53 LEN=393 TOS=0x00 PREC=0x00 TTL=48 ID=36498 PROTO=UDP SPT=30856 DPT=1026 LEN=373 
[ 4851.864000] Inbound IN=ppp0 OUT= MAC= SRC=201.9.179.194 DST=213.178.117.53 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=57911 DF PROTO=TCP SPT=61101 DPT=41972 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4853.776000] Inbound IN=ppp0 OUT= MAC= SRC=201.9.179.194 DST=213.178.117.53 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=58305 DF PROTO=TCP SPT=61101 DPT=41972 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4860.172000] Inbound IN=ppp0 OUT= MAC= SRC=201.9.179.194 DST=213.178.117.53 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=58855 DF PROTO=TCP SPT=61101 DPT=41972 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4941.440000] Inbound IN=ppp0 OUT= MAC= SRC=74.102.146.97 DST=213.178.117.53 LEN=394 TOS=0x00 PREC=0x00 TTL=45 ID=6595 PROTO=UDP SPT=30856 DPT=1026 LEN=374 
[ 5297.904000] Inbound IN=ppp0 OUT= MAC= SRC=78.52.192.194 DST=213.178.117.53 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=45208 PROTO=UDP SPT=64083 DPT=47134 LEN=70 
[ 6432.508000] Inbound IN=ppp0 OUT= MAC= SRC=200.55.106.47 DST=213.178.117.53 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=256 PROTO=TCP SPT=2870 DPT=5900 WINDOW=55808 RES=0x00 SYN URGP=0 
[ 6505.696000] Inbound IN=ppp0 OUT= MAC= SRC=78.52.193.46 DST=213.178.117.53 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=41113 PROTO=UDP SPT=64132 DPT=47134 LEN=70 
[ 6722.084000] Inbound IN=ppp0 OUT= MAC= SRC=35.148.31.201 DST=213.178.117.53 LEN=401 TOS=0x00 PREC=0x00 TTL=48 ID=1267 PROTO=UDP SPT=30856 DPT=1026 LEN=381 
woxom@Yellorange:~$ 


THANKS,


Tamas

---

### Post by koosfoto.hu on 2007-08-23
Sorry, schorsch!

The previous answer was fro U...

Tamas

---

### Post by koosfoto.hu on 2007-08-23
Hi ajgreeny,

There is only cdrom0 and floppy0.
Nothing else... helas.

Thanks,

Tamas

---

### Post by schorsch on 2007-08-23
> **koosfoto.hu said:**
> 
[ 4551.264000] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[ 4552.588000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[ 4552.592000] sdb: Write Protect is off
[ 4552.592000] sdb: Mode Sense: 03 00 00 00
[ 4552.592000] sdb: assuming drive cache: write through
[ 4552.604000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[ 4552.612000] sdb: Write Protect is off
[ 4552.612000] sdb: Mode Sense: 03 00 00 00
[ 4552.612000] sdb: assuming drive cache: write through
[ 4552.612000]  sdb:<6>usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4555.596000] usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4557.804000] usb 2-2.3: reset full speed USB device using uhci_hcd and address 7
[ 4559.236000] end_request: I/O error, dev sdb, sector 0
[ 4559.236000] printk: 13 messages suppressed.
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] [COLOR="Red"]ldm_validate_partition_table(): Disk read failed.[/COLOR]
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Buffer I/O error on device sdb, logical block 0
[ 4559.236000] Dev sdb: unable to read RDB block 0
[ 4559.236000]  [COLOR="Red"]unknown partition table[/COLOR]
[ 4559.236000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 4559.236000] sd 4:0:0:0: Attached scsi generic sg1 type 0

There seems to be a problem with partitioning on the USB Drive. The device itself is recognized as /dev/sdb but the partitions are not. I would advise to test it on a windows machine, if it works there backup your data, repartition the drive, reformat the partition and restore your data.

---

### Post by yogo on 2007-08-23
What I would do is install gpart/Gnome partition manager.

This will serve twofold, it allows you to format your USB device as this is not possible to do from a right click menu like in Windows and secondly if gparted sees your device, then you just have to mount it.

Chances are, you do not have a checked to automatically mount these devices.

---

### Post by Dr Small on 2007-08-23
> **yogo said:**
> What I would do is install gpart/Gnome partition manager.

This will serve twofold, it allows you to format your USB device as this is not possible to do from a right click menu like in Windows and secondly if gparted sees your device, then you just have to mount it.

Chances are, you do not have a checked to automatically mount these devices.
And to add on to yogo's statement, that can be done under System > Administration > Users and Groups and then go to Properties on your account and make sure you have permission to mount portable devices.

Dr Small

---

### Post by koosfoto.hu on 2007-08-23
Thanks for ALL!

It is a "simple" USB pen drive, withc changeble memory cards from my camera.
Fortunatelly I have copied it already to the notebook of a friend (with Windows). 
I have put into it another card... and it WORKED!

So, it seems to be a good idea, that the partition is bed.
THANKS!

I will reformat it when I have the data well saved (when my friends come here)... and see after again.

THANKS A LOT!
I highly appreciate your help!

Friendly greetings from Budapest,

Tamas

---

### Post by schorsch on 2007-08-23
Well, it's never nice to hear about a corrupt partition table .... but could you please mark this thread as solved as this could help others, too?

---

### Post by koosfoto.hu on 2007-08-23
Dear schorsch,

How can I mark this thread as solved?

THANKS,

Tamas

---

### Post by Dr Small on 2007-08-23
Go to the top, click "Thread Tools", then click, "Mark as Solved".

Dr Small

---

