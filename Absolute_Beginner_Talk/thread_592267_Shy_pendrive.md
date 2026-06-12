---
title: "Shy pendrive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-10-26
I have a Dual Boot; Win 2000/Gutsy. My Pen Drive doesn't show up in Gutsy?? I think the right 1st step is to:

nnjond@nnjond-desktop:~$ sudo fdisk -l
[sudo] password for nnjond:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa459283

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda2            3960       10011    48612690   83  Linux
/dev/sda3            2933        3959     8249377+   f  W95 Ext'd (LBA)
/dev/sda5            2933        3783     6835626   83  Linux
/dev/sda6            3784        3959     1413688+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31ac70c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   b  W95 FAT32
nnjond@nnjond-desktop:~$ 

Please advise me on what to do next?

P.S.
What's the diff between a pen and a flashdrive?

---

### Post by MegaJim on 2007-10-26
pen is a 'trendy' name for the same thing.

run "lshw" from a terminal as root to list your hardware

```
sudo lshw
```

check for your usb host controller and pen drive

---

### Post by Steve1961 on 2007-10-26
If your drive doesn't show up in the nautilus sidebar when you insert it try mounting it manually:

sudo mkdir tempdisk
sudo mount -t vfat /dev/sdb5 /mnt/tempdisk

then take a look in /mnt/tempdisk

---

### Post by MegaJim on 2007-10-26
> **Steve1961 said:**
> If your drive doesn't show up in the nautilus sidebar when you insert it try mounting it manually:

sudo mkdir tempdisk
sudo mount -t vfat /dev/sdb5 /mnt/tempdisk

then take a look in /mnt/tempdisk

unless he has a 160gb pen drive, i dont think thats going to help :)

---

### Post by Steve1961 on 2007-10-26
:lolflag:  I really should take the time to read properly.

Ok, insert the drive and then type the following

dmesg | tail

post the output here

---

### Post by nnjond on 2007-10-26
Thanks for your help. Do u know what this means?

nnjond@nnjond-desktop:~$ sudo mkdir tempdisk
nnjond@nnjond-desktop:~$ sudo mount -t vfat /dev/sdb5 /mnt/tempdisk
mount: mount point /mnt/tempdisk does not exist
nnjond@nnjond-desktop:~$

---

### Post by MegaJim on 2007-10-26
You might try

```
sudo lsusb
``` after insterting it as well, to check its been detected.

---

### Post by tekkenlord on 2007-10-26
try the following:

sudo mkdir /mnt/tempdisk
sudo sudo mount -t vfat /dev/sdb5 /mnt/tempdisk

then take a look at /mnt/tempdisk...

---

### Post by nnjond on 2007-10-26
nnjond@nnjond-desktop:~$ dmesg | tail
[   36.568351] Bluetooth: HCI socket layer initialized
[   36.579536] Bluetooth: L2CAP ver 2.8
[   36.579542] Bluetooth: L2CAP socket layer initialized
[   36.630071] Bluetooth: RFCOMM socket layer initialized
[   36.630348] Bluetooth: RFCOMM TTY layer initialized
[   36.630352] Bluetooth: RFCOMM ver 1.8
[   41.965821] NET: Registered protocol family 17
[   43.644645] NET: Registered protocol family 10
[   43.644833] lo: Disabled Privacy Extensions
[   54.248691] eth0: no IPv6 routers present
nnjond@nnjond-desktop:~$

---

### Post by MegaJim on 2007-10-26
please list the output of 

```
sudo lsusb
```

in code brackets if possible for easy reading, thanks

---

### Post by Steve1961 on 2007-10-26
> **nnjond said:**
> nnjond@nnjond-desktop:~$ dmesg | tail
[   36.568351] Bluetooth: HCI socket layer initialized
[   36.579536] Bluetooth: L2CAP ver 2.8
[   36.579542] Bluetooth: L2CAP socket layer initialized
[   36.630071] Bluetooth: RFCOMM socket layer initialized
[   36.630348] Bluetooth: RFCOMM TTY layer initialized
[   36.630352] Bluetooth: RFCOMM ver 1.8
[   41.965821] NET: Registered protocol family 17
[   43.644645] NET: Registered protocol family 10
[   43.644833] lo: Disabled Privacy Extensions
[   54.248691] eth0: no IPv6 routers present
nnjond@nnjond-desktop:~$


For some reason your system is not recognising a usb stick being inserted.  Are you sure the usb ports are working OK?

---

### Post by nnjond on 2007-10-26
nnjond@nnjond-desktop:~$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
nnjond@nnjond-desktop:~$ 

nnjond@nnjond-desktop:~$ sudo mkdir /mnt/tempdisk
nnjond@nnjond-desktop:~$ sudo sudo mount -t vfat /dev/sdb5 /mnt/tempdisk
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ sudo mkdir /mnt/tempdisk
mkdir: cannot create directory `/mnt/tempdisk': File exists
nnjond@nnjond-desktop:~$ sudo sudo mount -t vfat /dev/sdb5 /mnt/tempdisk
mount: /dev/sdb5 already mounted or /mnt/tempdisk busy
mount: according to mtab, /dev/sdb5 is already mounted on /mnt/tempdisk

Getting confused.

---

### Post by MegaJim on 2007-10-26
:) stop trying to mount your sdb, its already mounted, just forget about that.

Your problem is the pen drive isn't being detected, it could be:
1. Faulty pen drive
2. Faulty USB port
3. other problem

check by inserting the stick into a different port and checking

```
dmesg | tail
```
and
```
sudo lsusb
```

again.

---

### Post by Steve1961 on 2007-10-26
nnjond@nnjond-desktop:~$ sudo mkdir /mnt/tempdisk
nnjond@nnjond-desktop:~$ sudo sudo mount -t vfat /dev/sdb5 /mnt/tempdisk
nnjond@nnjond-desktop:~$
nnjond@nnjond-desktop:~$ sudo mkdir /mnt/tempdisk
mkdir: cannot create directory `/mnt/tempdisk': File exists
nnjond@nnjond-desktop:~$ sudo sudo mount -t vfat /dev/sdb5 /mnt/tempdisk
mount: /dev/sdb5 already mounted or /mnt/tempdisk busy
mount: according to mtab, /dev/sdb5 is already mounted on /mnt/tempdisk

Yes, ignore this bit, my fault.  This is a hard drive that's already mounted, not a usbstick.  The ouput of lsusb also looks like the stick isn't registering on the system.  Other than a faulty usb port I'm not sure what to suggest from here.

---

### Post by nnjond on 2007-10-26
I haven't touched the usb stick since it was recognised in Win 2000.

---

### Post by ddrichardson on 2007-10-26
Does any USB device work and on what hardware is it installed - some machines require the noirqdebug kernel parameter to recognise the USB hub.

---

### Post by MegaJim on 2007-10-26
His optical mouse is listed by lsusb so it seems that port is working.

Try plugging the usb stick straight into a port on your PC rather than through a hub (if that's what you're doing)

---

### Post by nnjond on 2007-10-26
Thanks for your help. I've tried all your sugestions but... 
It showed up from time to time in Edgy & Fiesty??

---

### Post by lespaul_rentals on 2007-10-26
Are you running Gnome or KDE?  When I would install KDE only I didn't have gnome-volume-manager installed, so my USB drives wouldn't open.

```
sudo apt-get install gnome-volume-manager
```
```
killall gnome-volume-manager
```
```
gnome-volume-manager
```

The insert your USB drive and see if that works.

---

### Post by llorch on 2007-10-31
First of all, excuse my English, I´m from Spain.
I have the same problem you have. It was in Feisty when my pen firstly failend to mount. Ubuntu just seems to ignore my pen exists. It does nothing. The I upgraded to Gutsy, but still the same problem. I´ve tried everything (every type of format, ntfs, Fat, Fat 32...), but it doesn´t work. It´s a 2gb Imation, buy lately I´ve tried a 4 gb and the same thing, nothing happens. And it´s not my usb port, as I have an external 100 gb HD that works perfectly well. 
 I´m desperated with this bug, it´s really embarrasing rebooting all the time and going to XP just to copy a single file in a pendrive.

---

### Post by bgochnauer on 2007-11-11
Similar problem, usb flashdrive not detected, but don't know what ehci_hcd is or how to fix.

brian@kubuntu-lp2:/usr/games$ sudo lsusb
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
brian@kubuntu-lp2:/usr/games$ dmesg |tail
[183302.996000] usb 4-4: new high speed USB device using ehci_hcd and address 51
[183304.508000] usb 4-4: new high speed USB device using ehci_hcd and address 56
[183305.264000] usb 4-4: new high speed USB device using ehci_hcd and address 58
[183309.548000] usb 4-4: new high speed USB device using ehci_hcd and address 74

Thanks,
Bbrian

---

