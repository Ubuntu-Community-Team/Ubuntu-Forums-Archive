---
title: "Dual Boot Instalation/GRUB problems (non-typical)"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Mantis2600 on 2007-04-02
I just tried to install kubuntu, and I'm having all sorts of problems.  On the first install, Windows ate GRUB, so I attempted to follow the guide to fix it from the live CD, except that > find /boot/grub/stage1 could not be found.  So I attempted to reinstall and now NTLDR appears to have disappeared, but I thought I got GRUB working, so it was okay temporarily.  Now upon reboot its hanging on "grub loading stage2."  My partitions are currently a mess, and I figure that after all this messing, that's what all this is about.  The fdisk printout is below:
> 
Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2648    21270028+   7  HPFS/NTFS
/dev/sda2            2649       24321   174088372+   f  W95 Ext'd (LBA)
/dev/sda5            2649       24321   174088341    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           40636      620181   292091152+   7  HPFS/NTFS
/dev/sdb2   *           1         204      102784+  83  Linux
/dev/sdb3             205        4365     2097144   82  Linux swap / Solaris
/dev/sdb4            4366       40635    18280080   83  Linux

Partition table entries are not in disk order


Disk one is Windows OS(sbd1) partition and File Storage(sbd2 and/or 5, I'm not sure what that's all about) and disk two is file storage (sbd1) a boot partition(sbd2) swap(sbd3) and the kubuntu partition (sbd4).




ANY help would be appreciated :)

:confused:

---

### Post by dstew on 2007-04-02
Boot from the live CD, go to a terminal, start grub, and try the find command again.

---

### Post by Mantis2600 on 2007-04-02
> grub> find /boot/grub/stage1

Error 15: File not found

Same error...

---

### Post by WelshChris on 2007-04-02
Hi Mantis.

The find command as stated in the how-to didn't seem to work for me either, so I hacked together menu.lst from intelligent guesses, which worked first time.

   I'd just like to suggest you try

find /grub/stage1

instead.  This seemed to work for me, since /boot is on it's own partition, which (I think) also applies to you.

wc

---

### Post by Mantis2600 on 2007-04-02
WelshChris,

You are correct, I did give the /boot its own small partition at the suggestion of a user on the IRC channel as a method to fix this issue.  Interestingly, its still here :-/.

I attempted that command and I also recived a file not found error.

---

### Post by dstew on 2007-04-02
Try **sudo grub** to start grub from the live CD, then the find command should work (Edgy Live CD).

---

### Post by Mantis2600 on 2007-04-02
Still nothing....but I am using a 6.06 LTS live CD, could that be the problem?

---

### Post by WelshChris on 2007-04-02
What's your /boot/grub/menu.1st file like?

wc

---

### Post by Mantis2600 on 2007-04-02
We may be getting somewhere...

That file doesn't exist and I can't mount any of my drives in the livecd.

---

### Post by dstew on 2007-04-02
Grub needs to be able to mount a partition to its own file system in order to find files, get geometry etc. If the drive is already mounted, grub won't be able to work on it. Could it be that the drives were already mounted on the live CD file system? If you do a fresh Live CD boot, does grub still not find the file? From the grub prompt, what do you get if you try **geometry (hd0)**?

Also, the name of the file you are looking for is /boot/grub/menu.lst, not menu.1st.

---

### Post by WelshChris on 2007-04-02
Can't mount your drives with the LiveCD?  Can you post the output of

df -hl      (as in hotel lima)

and

mount

wc

---

### Post by Mantis2600 on 2007-04-02
A fresh boot yields the same result.  Also:

```
grub> geometry (hd0)
drive 0x80: C/H/S = 496/16/32, The number of sectors = 253952, /dev/sdc
   Partition num: 0,  Filesystem type is fat, partition type 0x6

```

---

### Post by dstew on 2007-04-02
OK, grub can see your FAT disk, and thinks its name is /dev/sdc. So, we know that (hd0,0) is the same as /dev/sdc1. Now do: 

geometry (hd1)
geometry (hd2)

etc. to see how grub sees your drives and partitions. Hopefully we can find your linux partition, and set up grub correctly.

---

### Post by Mantis2600 on 2007-04-02
That's funny because I don't have anything formated with FAT...


```
grub> geometry (hd1)

Error 21: Selected disk does not exist

grub> geometry (hd2)

Error 21: Selected disk does not exist

grub>

```

---

### Post by dstew on 2007-04-02
OK, I'm lost. You have no FAT disk, and that is the only one grub sees. I give up. Anyone else have a clue?

---

### Post by Mantis2600 on 2007-04-02
Haha, your guess is as good as mine. I'm just disappointed that I can't get Kubuntu running :(

What gets me is that last time, I had NO trouble getting it installed.  I didn't keep it because it got replaced by something else I was tinkering with.  Now, its not working at all, and it looks like it took NTLDR with it. Needless to say, i don't know enough about linux to try to solve this myself.

---

### Post by Mantis2600 on 2007-04-02
HereChris,

```
ubuntu@ubuntu:~$ df -hl
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.1G  624M  479M  57% /
varrun                506M   88K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  156K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  8.8M  498M   2% /lib/modules/2.6.15-23-386/volatile
tmpfs                 506M  844K  506M   1% /tmp
/dev/sdc1             124M   26M   98M  22% /media/sdc1

```

and

```
ubuntu@ubuntu:~$ mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/sdc1 type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

```

---

### Post by Mantis2600 on 2007-04-02
/dev/sdc1 is likely my thumbdrive, it's currently plugged in and would make since as it is my only other "drive"

---

### Post by dannyboy79 on 2007-04-02
please post the output from 

lspci -v

and

sudo cat /etc/modules

we need to find out what sata controller you have! we also need to find out what version of ubuntu you tried before and was it with the same hardware and situation, ie: dual booting same drives etc etc.

---

### Post by Mantis2600 on 2007-04-02
Here you are sir:

```
ubuntu@ubuntu:~$ lspci -v
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at e400 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 2000 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at fd003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at fd004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at fd005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at fd000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Giga-byte Technology: Unknown device a002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at bc00 [size=256]
        I/O ports at c000 [size=128]
        Memory at fd001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at e000 [size=128]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 50000000-500fffff

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology: Unknown device 310f
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: Giga-byte Technology Marvell 88E8001 Gigabit Ethernet Controller (Gigabyte)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 217
        Memory at fc000000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at 9000 [size=256]
        Expansion ROM at 50080000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:0d.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
        Subsystem: Silicon Image, Inc. SiI 3512 SATALink Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 185
        I/O ports at 9400 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9c00 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at a400 [size=16]
        Memory at fc009000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 50000000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at fc008000 (32-bit, non-prefetchable) [size=2K]
        Memory at fc004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

```


and

```
ubuntu@ubuntu:~$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ubuntu@ubuntu:~$

```


Both Tries have been from the same 6.06LTS LiveCD with the same hardware.  The partitioning situation has sice changed because I've been trying different things in the process of troubleshooting.

---

### Post by dstew on 2007-04-02
It looks like grub cannot see your SATA disks because they are a RAID. Here is a link about installing on a RAID. I have not done this, so I can't say if it works, but maybe this is what you are going to have to do. Sorry.

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by Mantis2600 on 2007-04-02
Why on earth is it reporting my drives as a RAID configuration?  That's very odd...I'll take a look around.

---

### Post by Mantis2600 on 2007-04-02
I can't seem to find dmraid the guide calls for...I'm using Adept, I believe I enabled universe, but there's no dmraid.


edit- I think I know what I'm doing wrong

---

### Post by WelshChris on 2007-04-02
What's odd is that you can't mount any partition from your LiveCD.  As soon as I mounted my / partition, grub recognized everything, and found stage1 using
find /grub/stage1

---

### Post by Mantis2600 on 2007-04-02
```
sudo dmraid -ay
```
Returned saying there are no RAID devices

---

### Post by Mantis2600 on 2007-04-02
bumped, Anyone else have any other ideas?

---

### Post by dstew on 2007-04-02
Maybe there is some BIOS setting that affects how your disks are seen. Grub takes its disk information from the BIOS, rather than getting it all by itself, like the kernel does. Is it possible that the BIOS is treating them as a RAID in some way that makes them invisible to grub? Boy, am I out of my league here...

---

### Post by Mantis2600 on 2007-04-02
An update:  A friend on campus suggested that I try again with 6.10 and a fresh install.  It went well...that is until I booted into windows.  Now it's right back to skipping GRUB and grub not being found in the exact same way as it was in the beginning.  At least I can confirm that both installs are working, it's just a GRUB problem now.


edit-  ```
sudo grub
```  and find /grub/stage1 worked :)

---

### Post by Mantis2600 on 2007-04-02
spoke to soon, 

```
root (hd1,1)  and setup (hd1,1)
```

Didn't bring GRUB back, it loaded directly into windows upon boot.  I'm stumped.

---

### Post by confused57 on 2007-04-03
> **Mantis2600 said:**
> spoke to soon, 

```
root (hd1,1)  and setup (hd1,1)
```

Didn't bring GRUB back, it loaded directly into windows upon boot.  I'm stumped.

You might want to try:
root (hd1,1)
setup (hd1)

Then go into bios and set your drive with Ubuntu to boot before your Window's drive, if you get a grub menu at boot, highlight your Ubuntu entry, press "e", then change root to (hd0,1), press "b" to boot...post back if this works, there's a few other things you'd need to do to get your dual boot configured....may not work, but worth trying.

---

### Post by Mantis2600 on 2007-04-03
That appears to have worked.

---

### Post by confused57 on 2007-04-03
> **Mantis2600 said:**
> That appears to have worked.

If you want to make this permanent, you'll need to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Change the root in your Ubuntu entries to (hd0,1).

You'll also need to change this line:

```
# groot=(hd1,1)
```
to
```
# groot=(hd0,1)
```

In order to boot Windows from grub, you might need an entry similar to the one in the 3rd link in my signature.

If you want your system set up this way(booting first to sdb), then you might need to change your device.map:
```
gksudo gedit /boot/grub/device.map
```

you should probably change it to something like this:
```
(hd0) /dev/sdb
(hd1) /dev/sda
```

in order to get Windows to boot.

Added:  I believe when you first installed 6.06 that grub installed to sdc?

---

### Post by dannyboy79 on 2007-04-03
with newer motherboards that have sata raid ports, there is a setting in the bios that either will set the ports as raid or as "ide" (more or less, NOT raid) so, is this something that you did end up changing in the bios? glad you got it working but we need to understand why, if all you did was do an install of 6.10 ,that doesn't make any sense as 6.10 didn't change anything in regards to the issue you were having. UNLESS they added a newer libata which not supports your sata controller. that has to be it. were you using the sata ports hooked to the CK8S Serial ATA Controller or were you using the sata ports hooked to the SiI3512 raid controller? I am not sure about the nForce controller but according to here ([http://ubuntuforums.org/showthread.php?p=1872506](http://ubuntuforums.org/showthread.php?p=1872506)) 2.6.15 kernel (default kernel in Dapper) does support the SiI3512, so maybe try those ports and Dapper again to troubleshoot this for everyone else. I would like to as I am about to buy a PCI card w/ the SiI3512 from newegg.com for $11.99 (2 ports) and I would really appreciate if you could tell me first hand that Dapper does support this controller.

---

### Post by dstew on 2007-04-03
I agree with dannyboy79, it would be nice to know why grub did not see the drives at all in your first installation, but now it does. Did you change any bios settings?

---

### Post by Mantis2600 on 2007-04-03
> **dannyboy79 said:**
> with newer motherboards that have sata raid ports, there is a setting in the bios that either will set the ports as raid or as "ide" (more or less, NOT raid) so, is this something that you did end up changing in the bios? glad you got it working but we need to understand why, if all you did was do an install of 6.10 ,that doesn't make any sense as 6.10 didn't change anything in regards to the issue you were having. UNLESS they added a newer libata which not supports your sata controller. that has to be it. were you using the sata ports hooked to the CK8S Serial ATA Controller or were you using the sata ports hooked to the SiI3512 raid controller? I am not sure about the nForce controller but according to here ([http://ubuntuforums.org/showthread.php?p=1872506](http://ubuntuforums.org/showthread.php?p=1872506)) 2.6.15 kernel (default kernel in Dapper) does support the SiI3512, so maybe try those ports and Dapper again to troubleshoot this for everyone else. I would like to as I am about to buy a PCI card w/ the SiI3512 from newegg.com for $11.99 (2 ports) and I would really appreciate if you could tell me first hand that Dapper does support this controller.

The only change I made in BIOS was telling sdb to boot before sda, however this change was made BEFORE I installed Ubuntu 6.10 instead of Kubuntu 6.06LTS, so while it may have contributed to helping, it can't be the only reason.I have no idea which sata controller I'm connected to...I'm not sure which SATA controller I'm plugged into...I don't have the documentation for my motherboard so I'm not sure which is which.  If I had to guess, I'd say its probably the NForce controller, but I can't be sure.

---

