---
title: "USB Flash don't work (In other OS too)."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Tvinky on 2007-06-26
I got problem with my USB Flash 1GB memory. Some days before i could just plug it in and it worked (mounted automaticly). It worked on Ubuntu, other distributes and Win too. But now when I plug it in, flash memory show's that it have power, but nothing else. It's not mounting not in win, and Ubuntu. I know, maybe it's not the right place where to write about this problem, but maybe someone could help me with some advices. How it can be, that power is going to flash memory, but I can't mount it ;( I have tryed another flash device, with photo card, but it didn't work too...

**lsusb**
```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

**mount**
```

/dev/hda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/hda5 type vfat (rw,utf8,umask=007,gid=46)
/dev/hdb1 on /media/hdb1 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

**df -h**
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             6.4G  2.7G  3.4G  45% /
varrun                126M   72K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb            126M  108K  125M   1% /proc/bus/usb
udev                  126M  108K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   33M   93M  27% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1             4.2G  3.8G  415M  91% /media/hda1
/dev/hda5             7.9G  7.2G  631M  93% /media/hda5
/dev/hdb1              39G   27G   13G  69% /media/hdb1

```

**lspci**
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0b.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)

```

**dmesg | grep usb**
```

dmesg | grep usb
[   22.599772] usbcore: registered new interface driver usbfs
[   22.599807] usbcore: registered new interface driver hub
[   22.599844] usbcore: registered new device driver usb
[   25.113426] usb usb1: configuration #1 chosen from 1 choice
[   25.219823] usb usb2: configuration #1 chosen from 1 choice
[   25.327864] usb usb3: configuration #1 chosen from 1 choice

```


I think that maybe it's not an OS problem. But how can i fix it? BIOS? (But why power is going to flash). If it would be disabled in BIOS, power would not go to device. (I think...)

P.S Sorry about my language, i'm not english.

---

### Post by Super TWiT on 2007-06-26
Does it work if you put the usb key in as soon as you start the computer?

---

### Post by Tvinky on 2007-06-26
> **Super TWiT said:**
> Does it work if you put the usb key in as soon as you start the computer?

You mean put device in when computer is starting up? I'll try.

Edited: Tryed, but no results. I put in my flash device when I was in Ubuntu 7.04, made restart and with restart the red light on my flash drive disapiered. And with boot in again didn't show up :P So, I get my flash out, and again in - and the red light showed up - but usbdrive is not mounting ;( I don't know, maybe it's something wrong happened with my USB ports... If noon can give some advice what to do, I will try to reinstall my system, maybe it will help. (But I don't believe in this, beacause Win don't mount flash and other devices too). ;(

---

### Post by Super TWiT on 2007-06-26
It might also be the flash drive.  Could you plug it into another computer to see if it works there?

---

### Post by Tvinky on 2007-06-29
> **Super TWiT said:**
> It might also be the flash drive.  Could you plug it into another computer to see if it works there?

I know that flash drive is ok, because my friend has comed to me with his flash drive and it didn't worked for me. But when he get back home, his flash drive was working ;(

---

### Post by Super TWiT on 2007-06-29
It sounds like the drive might need to be reformatted.  Doing so will destroy all the data on the drive, but it would probably work again.  A good program to do this is gparted.  It is in the universe repositories.  ```
 sudo apt-get install gparted
```then typing in ```
sudo gparted
```  You can select which device to scan for partitions in the top right corner.  If it still dosen't show up you may want to download the livecd version: [http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=osdn&filename=gparted-livecd-0.3.4-8.iso&43353920](http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=osdn&filename=gparted-livecd-0.3.4-8.iso&43353920).  This will boot off of a cd.

---

