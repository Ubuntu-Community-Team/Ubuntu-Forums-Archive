---
title: "cd rom drive worked on 9.04 but not in 9.10 ?"
date: 2009-11-11
forum: Apple Hardware Users
---

### Post by davidy67 on 2009-11-11
hi, i had Ubuntu 9.04 installed on my Mac Mini G4 system and have now burned and updated to 9.10, the cd rom drive is not detected upon reboot and install from live cd, dont have a clue why it worked in 9.04 and not 9.10 after reboot from live cd install.

thanks in advance

---

### Post by NoBugs! on 2009-11-12
Can you start from a different livecd? If no bootable cds work, it may be an Apple-efi bug. See [http://ubuntuforums.org/showthread.php?t=1090160](http://ubuntuforums.org/showthread.php?t=1090160)

---

### Post by davidy67 on 2009-11-13
dont think thats the solution, im trying to say that i have installed 9.10 but after it is installed to the hard drive and run from there it can not see any cd or dvd in the drive, the fstab file is the same configuration as it was when i was running 9.04 which i have now downgraded too for now because i need the cd rom drive for dvds and audio cds.

---

### Post by zts-it on 2009-12-14
> **davidy67 said:**
> hi, i had Ubuntu 9.04 installed on my Mac Mini G4 system and have now burned and updated to 9.10, the cd rom drive is not detected upon reboot and install from live cd, dont have a clue why it worked in 9.04 and not 9.10 after reboot from live cd install.

thanks in advancesame problem and also on Mac Mini G4. Got audio/music CDs to load by installing *CD Player 2.0.0*, but DVDs are no go. The CD/DVD drive itself is detected on boot, but it seems it's always "empty" when you insert a DVD. These are the specs detected:
---------          
    description: Computer
    product: Mac mini
    vendor: Copyright 1983-2004 Apple Computer, Inc. All Rights Reserved
    serial: xxxxxxxxxxx
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
       clock: 166MHz
       capabilities: powermac10_1 macrisc3 power_macintosh
     *-firmware
          product: OpenFirmware 3
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-memory
          description: System memory
          physical id: 1
          size: 1GiB
        *-bank
             description: DDR SDRAM
             product: PC2700U-25330
             physical id: 0
             version: 0000,05 02,00
             serial: K
             slot: DIMM0/J11
             size: 1GiB
     *-cpu
          description: CPU
          product: 7447A, altivec supported
          physical id: 2
          bus info: cpu@0
          version: 1.2 (pvr 8003 0102)
          size: 1249MHz
          clock: 166MHz
          capabilities: altivec performance-monitor
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 512KiB
             clock: 1249MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: UniNorth 2 AGP
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: RV280 [Radeon 9200]
             vendor: ATI Technologies Inc
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: agp agp-2.0 pm bus_master cap_list rom
             configuration: driver=radeonfb latency=255 mingnt=8
             resources: irq:48 memory:98000000-9fffffff(prefetchable) ioport:400(size=256) memory:90000000-9000ffff memory:90020000-9003ffff(prefetchable)
     *-pci:1
          description: Host bridge
          product: UniNorth 2 PCI
          vendor: Apple Computer Inc.
          physical id: 101
          bus info: pci@0001:10:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-generic
             product: KeyLargo/Intrepid Mac I/O
             vendor: Apple Computer Inc.
             physical id: 17
             bus info: pci@0001:10:17.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=macio latency=16
             resources: irq:0 memory:80000000-8007ffff
           *-ide
                description: IDE Channel 0
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
        *-usb:0 UNCLAIMED
             description: USB Controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Computer Inc.
             physical id: 18
             bus info: pci@0001:10:18.0
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0 maxlatency=86 mingnt=3
        *-usb:1 UNCLAIMED
             description: USB Controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Computer Inc.
             physical id: 19
             bus info: pci@0001:10:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0 maxlatency=86 mingnt=3
        *-usb:2
             description: USB Controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Computer Inc.
             physical id: 1a
             bus info: pci@0001:10:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3
             resources: irq:29 memory:80083000-80083fff
        *-usb:3
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 1b
             bus info: pci@0001:10:1b.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1
             resources: irq:63 memory:80082000-80082fff
        *-usb:4
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 1b.1
             bus info: pci@0001:10:1b.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1
             resources: irq:63 memory:80081000-80081fff
        *-usb:5
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 1b.2
             bus info: pci@0001:10:1b.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=16 maxlatency=34 mingnt=16
             resources: irq:63 memory:80080000-800800ff
     *-pci:2
          description: Host bridge
          product: UniNorth 2 Internal PCI
          vendor: Apple Computer Inc.
          physical id: 102
          bus info: pci@0002:20:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-generic
             product: UniNorth/Intrepid ATA/100
             vendor: Apple Computer Inc.
             physical id: d
             bus info: pci@0002:20:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ide-pmac latency=32
             resources: irq:39 memory:f5004000-f5007fff
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: ST940110A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.07
                   serial: 3KW4TMFS
                   size: 37GiB (40GB)
                   capacity: 37GiB (40GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:mac
                   configuration: apm=off smart=on
                 *-volume:0
                      description: Apple partition map
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 31KiB
                 *-volume:1
                      description: Apple Bootstrap
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 974KiB
                      capacity: 977KiB
                      capabilities: bootable hfs initialized
                      configuration: created=2009-12-13 01:31:41 filesystem=hfs label=bootstrap modified=2009-12-13 01:31:42 state=clean
                 *-volume:2
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      logical name: /
                      version: 1.0
                      serial: e1ba674c-5ba2-47cd-b64a-f5534fe12fc3
                      size: 35GiB
                      capacity: 35GiB
                      capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2009-12-13 01:14:01 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;US&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;&#62793;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;U modified=2009-12-13 01:34:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-12-13 01:57:13 state=mounted
                 *-volume:3
                      description: Linux swap volume
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      version: 1
                      serial: a3b67b6e-51cc-422b-bc33-9f3ac457fded
                      size: 1611MiB
                      capacity: 1611MiB
                      capabilities: swap initialized
                      configuration: filesystem=swap pagesize=4096
             [B] *-cdrom
                   description: DVD reader
                   product: MATSHITACD-RW CW-8123
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: CAD4
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2 status=open[/B]
        *-firewire
             description: FireWire (IEEE 1394)
             product: UniNorth 2 FireWire
             vendor: Apple Computer Inc.
             physical id: e
             bus info: pci@0002:20:0e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12
             resources: irq:40 memory:f5000000-f5000fff
        *-network
             description: Ethernet interface
             product: UniNorth 2 GMAC (Sun GEM)
             vendor: Apple Computer Inc.
             physical id: f
             bus info: pci@0002:20:0f.0
             logical name: eth0
             version: 80
             serial: 00:11:24:33:b1:f6
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.19 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
             resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)
--------------------
I'll probably mess with it for a few more hours and if no success then I'll try Fedora 12 for PPC and see if I have any better luck.

---

### Post by DBMiller on 2009-12-14
I've just installed 9.10 on my eMac. Everything seems to work just great but no DVD/CD drive.  I put in a data dvd and the system won't open it. All I can get is the option to format the disk. 
I was going to replace the drive, it is old and won't open on it's own anymore, but I see this is an Ubuntu issue.
It would be great to get this resolved.
DBMiller

By the way, this is my first Ubuntu.

---

### Post by linuxopjemac on 2009-12-14
It sounds like a serious bug in Karmic's ppc version.

---

### Post by linuxopjemac on 2009-12-14
It's not only ppc apparently, searching through the forums I found this one:
[http://ubuntuforums.org/showthread.php?p=8458028](http://ubuntuforums.org/showthread.php?p=8458028)

solution might be here:
[http://ubuntuforums.org/showthread.php?t=1289478&highlight=automount+cdrom](http://ubuntuforums.org/showthread.php?t=1289478&highlight=automount+cdrom)

---

### Post by zts-it on 2009-12-14
> **linuxopjemac said:**
> It sounds like a serious bug in Karmic's ppc version.Yes. Karmic runs perfectly on my Intel PC notebook with no CD/DVD problems. It seems it's just PPC version (and maybe AMD too). Loading Fedora 12 for PPC just to see if CD/DVD works there.

---

### Post by zts-it on 2009-12-15
Couldn't resolve the CD/DVD automount problem in the 9.10 for PPC. Fedora 12 for PPC ...  same issue as Karmic plus it's much slower than Ubuntu at least on this MacMini G4. For some reason I couldn't boot up from Ubuntu 9.04 CD ... maybe a damaged media. However, I loaded the latest Debian 5.0.3 for PPC (lenny) and no problems whatsoever. All media is mounting correctly. I'm still puzzled tho why the 9.10 is working perfectly fine on my Intel PC notebook (ASUS G1) but has this media recognition problem in the PPC version.

---

### Post by brunoscunha on 2009-12-27
I have the same issue. Karmic does not recognize my laptops cd/dvd drive. I had to install karmic from an external usb disk.
The cd/dvd does not shows up on fstab

---

### Post by migel_wimtore on 2010-01-03
Similar issue with ibook G4. Everything was rosy (disk drive wise) in 9.4, now nothing. There is no icon on the desk-top or any evidence of the CD wherever i know where to look, though it does eject with the eject button and installed flawlessly from LiveCD- detected disk drive no probs (which it didnt with 8.10). Weird.
Been on ubuntu a week now and plan never to switch back to mac (over priced and over rated) so a fix would be great.
Also, there is no CD drive icon in my places menu, which i think there was in 9.4 and previous.

Cheers everyone.

---

### Post by redwoodguy on 2010-01-03
I'm not sure how I got this info, but I thought ONLY 9.04 has been made to run on PPC Mac. I installed 9.04 easily on my G4 ball, then tried to upgrade to 9.10 using the Upgrade manager, and it toally BLEW sky high. I had to revert to 9.04, which is working 99% fine.

---

### Post by migel_wimtore on 2010-01-03
Hi redwoodguy, i thought the same thing (though i dont know why), and trying to upgrade through update manager also totally locked-up my machine and on reboot was sort of half installed and really faulty, but did an install from 9.10 alternate liveCD (the main disc image was too big for an 80min CD) and it installed perfectly (actually has less noticeable issues than 9.4). Other than the disc drive issue and problems with trying to install all available security updates at once through update manager (there was over 150 and it locked up my machine trying to process them all, so i did them 20 at a time) shes running beautifully. Plus of course she still wont wake from hibernate or suspend, but that was the case in 9.4 as well anyways.

Get it here: [http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/) 
Go for the alternate if you find the main one wont fit on CD

Give it a go and let us know how it went.

Cheers.

---

### Post by koenigdererdmaennchen on 2010-01-05
Yust another confirm: karmic does not recognize media insertion into superdrive (MATSHITADVD-R)  on PowerBook G4 17" 1.67GHz, although listed in dmesg. This used to work in Jaunty.

---

### Post by Zabadda on 2010-01-08
yeh im having the same issue after installing 9.10 on a G5 tower, the cd boots live and the install is perfect but on booting into the hard drive it wont mount the media drive.

Is the solution to go back to 9.04? or is anyone using another Linux they can share with us?

---

### Post by migel_wimtore on 2010-01-08
Though there is no disc icon on the desktop when media is inserted i am getting CD playback in VLC ("Open Disc..." in Media drop down menu) as well as XINE and GNOME-Mplayer, though the latter two take a while to recognize media. 

Getting broken DVD playback for a region 2 disc (but nothing for another) and perfect playback for a region 0 DVD in VLC as well as a very old region 2. 
Getting the sound from one region 2 DVD in GNOME-Mplayer, broken playback for another and near perfect playback for the region 0 and the very old region 2, except for a white line down the screen and allot of noise from the disc-drive. 
Whilst XINE thinks most of the region 2 DVDs i inserted are crypted, but plays-back the region 0 proper smooth, as well as the old region 2.

Disk Utility recognises disc-drive (though says "unrecognised") and inserted media (also unrecognised).

So, CD playback is possible through VLC, XINE and GNOME-Mplayer.
DVD playback is touch and go, but possible with certain discs and certain apps. Perhaps there is an app out there that will play all DVDs though. Anyone know what it is?????

PS- i am getting slightly clicky sound during playback, but also get this for internet vids, wasnt getting this in 9.4 or 8.10, but had asumed it was something to do with my speakers personally (one of which i broke when opening my machine, perhaps i mashed something up in there that 9.10 is picking up on but which OSX and previous Ubuntu distros didnt) as sound playback via a USB soundcard (imic) through external speakers is perfect. Or has anyone else been experiencing clicky sound in 9.10 through built in speakers???

---

### Post by migel_wimtore on 2010-01-08
"sudo mount /dev/hdc" to mount explicitly through the terminal (common knowledge im sure but im very new to gnu/linux so forgive me). This gets the disc icon to appear on the desktop, though unfortunately playback is still hit and miss, as before.
Also, "sudo umount /dev/hdc", (note: umount, not uNmount, which had me scratching my head for a sec) must be entered in terminal before the eject button is effective- the right click menu wouldnt let me unmount from it and wanted root privileges (though this could be because i resonantly reinstalled ubuntu over the wrong partition, as i didnt know what i was doing, or because i made some other misstep during install, or is any one else having that message?).

CDs are actually fine for me, but is any one out there getting reliable dvd playback on a ppc running 9.10, or who knows how to get it???

Edit: sorry for all my text on this page.

---

### Post by koenigdererdmaennchen on 2010-01-14
I've filed a bug report [Bug #507113]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507113"). Please feel invited to confirm to raise chances that this problem will be solved some day.
Thanks!

---

### Post by the wizard of oz on 2010-03-05
Same problem here with an iBook G3.

---

### Post by conal on 2010-04-12
I have 9.10 running on two ppc's: 

I fixed the cd/dvd mount problem on my G4 iMac by installing Kubuntu and switching to KDE as my default window manager. Installing KDE fixed some other problems too, e.g auto-mounting a shared partition on my hard drive - no idea why! I have kept gnome and when I switch back to it the problems remain.

In short, I recommend Kubuntu on these models! 

However I am still looking for a solution on my old G3 iMac as KDE will be too heavy for this and I'm not getting CD/DVD recognition in XFCE or LXDE. I tried Fedora 12 on the G3 but it hangs during install.

Cheers

Conal

---

### Post by koenigdererdmaennchen on 2010-05-29
After upgrade to Lucid, the problem is even worse: I even cannot mount by hand any longer: sudo mount /dev/hdb first seems to work fine and i see the media contents in nautilus for a few second, but then the C/DVD is unmounted by something...
NO trace in the logs, as you might expect. 
What a mess...

---

### Post by koenigdererdmaennchen on 2010-06-01
If the above should happen to you, check your /etc/fstab **and remove the entry for your cd/dvd drive. **Then it's possible to mount manually at least. Aha.

---

### Post by sha.goyjo on 2010-06-01
> **koenigdererdmaennchen said:**
> After upgrade to Lucid, the problem is even worse: I even cannot mount by hand any longer: sudo mount /dev/hdb first seems to work fine and i see the media contents in nautilus for a few second, but then the C/DVD is unmounted by something...
NO trace in the logs, as you might expect. 
What a mess...

Is it that there is nothing in the logs recognizing the drive (i.e. including dmesg), or nothing in the logs recognizing the insertion of a disk? That might help for bug hunting.

Please note that I'm asking this before having read the whole launchpad thread! :P

EDIT:
Alright, I've finished reading the Launchpad Report and I'm still confused. Is the drive itself recognized by the system, and the disks aren't mounting...or not?

---

### Post by koenigdererdmaennchen on 2010-06-06
The drive is recognized by the kernel (dmesg) and even udisks (--enumerate), but the insertion of a disk leaves no traces in the log and the disks are not mounted. I guess uevents are somehow not propagated from the PPC kernel to udisks...

---

### Post by koenigdererdmaennchen on 2010-06-06
First progress (for me): insert a disk into the drive and then issue the following command on the terminal (either as root or per sudo):
**udisks --poll-for-media** *<your device goes here>*
(where *<your device goes here>* must be replaced by the appropriate device, i.e., /dev/hdb in my case) and the disk appears as by magic. Eject / unmount then works as expected. 
To my experience, you should repeat this command every time after the content of the drive changed to make it work properly.

I suggest to  put the command into a little shell script on your shelf to have it at hand (as i did).

EDIT:
I filed a new bug report #590448 (_[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448)_) including these observations. I hope this receives more attention than the previous one...

---

### Post by sha.goyjo on 2010-06-06
This is HAWT news beyond compare koenig. Unfortunately the udisks poll command only works for me once per boot before failing without any error message. Any clues?

---

### Post by koenigdererdmaennchen on 2010-06-08
> **sha.goyjo said:**
> This is HAWT news beyond compare koenig. Unfortunately the udisks poll command only works for me once per boot before failing without any error message. Any clues?
I have to run the command not only after a disc was inserted, but also after it has been ejected. Then it works as often as desired. 
If this does not help, try to kill the process:
1) Determine process number by 
ps aux | grep udisks
On my machine, the poll process looks like:
root      1238  0.0  0.0   7172  1036 ?        S    Jun07   0:00 udisks-daemon: polling /dev/hdb
2) Kill it via process number:
sudo kill 1238
3) repeat the poll command from my previous post.
HTH

P.S.: Please consider to confirm my bug report #590448 (_[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/590448)_). Thanks.

---

### Post by sha.goyjo on 2010-06-08
Confirmed.

---

### Post by 330P4 on 2011-10-25
This is a known bug with Ubuntu powerpc distros beginning with Karmic 9.10

I have personally tried 10.04 and 10.1

9.04 PLAYS CDs but not easily

6.06 Dapper Drake Plays CDs easily....

My Lombard PB G3/333 (1999) has a newer Pismo (2000) DVD-ROM drive.

512MB RAM

30GB HDD

Orinoco Silver 802.11b Cardbus wifi mimics Airport...

I've been a MACSTER since 1997...

Mac recycler since 2000

J.C.

---

