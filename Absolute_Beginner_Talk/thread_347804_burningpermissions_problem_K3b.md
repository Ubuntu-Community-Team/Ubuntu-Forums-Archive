---
title: "burning/permissions problem K3b"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Daemion_AF on 2007-01-27
Im having trouble trying to burn with k3b, It is saying that i do not have permissions however i go to the k3bsetup2 and click my drive and apply and it still says it doesnt have permissions. Is  there a manual way to open the drive for access?

---

### Post by taurus on 2007-01-27
Do you belong to group cdrom?  What's the output of this command from a terminal?

applications -> Accessories -> Terminal
```
id
```

---

### Post by Daemion_AF on 2007-01-27
uid=1000(daemion) gid=1000(daemion) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(daemion)

---

### Post by Daemion_AF on 2007-01-27
ttt any help?

---

### Post by Daemion_AF on 2007-01-28
Can anyone please figure this out, it turns out its not just k3b it does it with gnomebake as well.

---

### Post by Daemion_AF on 2007-01-28
here is my debug message if it helps

/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
:confused:

---

### Post by taurus on 2007-01-28
Can you paste the whole output of this command here?

```
dmesg | more
(Hit the space bar for the next 24 lines.)
```
But looks like there could be a problem with your CD burner.

---

### Post by Daemion_AF on 2007-01-28
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-686
Devices
-----------------------
SONY DVD+-RW DW-Q58A UDS1 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=24 -dao driveropts=burnfree -eject -data /home/daemion/Desktop/ubuntu-6.06.1-alternate-i386.iso

---

### Post by vicnov on 2007-03-06
You can resolve permissions issue by the following command:
```
sudo chown root:cdrom /dev/sg0
```
(for me it was /dev/sg1)

And also check that you are a member of "cdrom" grop by typing "id" command.

If it helps, you may add this command to /etc/rc.local to enable it each time the system boots.

---

