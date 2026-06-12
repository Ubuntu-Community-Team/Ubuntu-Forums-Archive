---
title: "New Intel iMac Install How-to"
date: 2007-09-05
forum: Apple Intel Users
---

### Post by dchart on 2007-09-05
I have one of the new, metallic 20" iMacs, and I'm typing this from within Ubuntu on it. So here's what I did.

1) Boot up Mac OS, and enjoy the big screen and bright colours by playing DVDs. This is possibly not an essential step, but you know you want to...

2) Download, and burn, lots of Ubuntu CDs. The one you actually want is Gutsy Gibbon Tribe 5 i386. Feisty doesn't get through boot, and Gutsy 5 amd64 works from the CD, but X crashes after you actually install.

3) Start up from the Mac DVDs. Use Disk Utility (on the Utilities menu) to repartition the hard drive, leaving free space. I made lots of space for later installations.

4) Reinstall MacOSX onto the first partition.

5) Reboot to the Ubuntu Live CD.

6) Install. Use the manual partitioner to make Linux partitions. Choosing to use the free space would probably also work, but that's not actually what I did. Just follow the instructions.

7) Reboot. You will go straight into MacOS X.

8) Download and install rEFIt. Just double click the installer.

9) Reboot. You should have Linux on your menu, and it should just work.

Really, really easy, if you ignore the time I spent testing disks that ultimately didn't work...

---

### Post by cyberdork33 on 2007-09-05
> **dchart said:**
> 3) Start up from the Mac DVDs. Use Disk Utility (on the Utilities menu) to repartition the hard drive, leaving free space. I made lots of space for later installations.

Just note on this step you can do several things to get the partitioning done. If you do not want to reinstall OSX, you can use gparted to resize the volume or even bootcamp.

Also for those that want to triple boot, it is best to install grub to the linux boot partition instead of the MBR as stated elsewhere.

Thanks for your post dchart! I am interested in the X errors when using 64 bit. Did you file a bug report?

---

### Post by dchart on 2007-09-05
> **cyberdork33 said:**
> 
Thanks for your post dchart! I am interested in the X errors when using 64 bit. Did you file a bug report?

No. I don't have enough information, beyond "X doesn't work and exits with signal 11 on boot", and from experience people would be asking for stack traces. Right now, I don't have enough time to provide the feedback necessary to get it to work.

One note: sound does not appear to work. That doesn't bother me, and seems to be a very common problem, so I've not put any effort into trying to solve it yet (beyond checking that the master volume wasn't just muted).

---

### Post by cyberdork33 on 2007-09-05
> **dchart said:**
> No. I don't have enough information, beyond "X doesn't work and exits with signal 11 on boot", and from experience people would be asking for stack traces. Right now, I don't have enough time to provide the feedback necessary to get it to work.

One note: sound does not appear to work. That doesn't bother me, and seems to be a very common problem, so I've not put any effort into trying to solve it yet (beyond checking that the master volume wasn't just muted).
Actually, on the newer kernel (2.6.22.6), I found that the Master channel does absolutely nothing on mine. Front and PCM adjust the volume levels. You can also try flipping switches such as "line in as output" as there were issues similar to this before with feisty.

Also, if you could post the output of lspci, we could see the hardware changes.

---

### Post by dchart on 2007-09-05
> **cyberdork33 said:**
> Actually, on the newer kernel (2.6.22.6), I found that the Master channel does absolutely nothing on mine. Front and PCM adjust the volume levels. You can also try flipping switches such as "line in as output" as there were issues similar to this before with feisty.

Also, if you could post the output of lspci, we could see the hardware changes.

Thanks for the sound hints. I'll have a look at them when I have a spare moment.

lspci looks like this:

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9583
03:00.0 FireWire (IEEE 1394): Agere Systems Unknown device 5901 (rev 05)
04:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 436a (rev 13)

---

### Post by mauro on 2007-09-21
About the keyboard, how to control the brightness of the monitor?

---

### Post by cyberdork33 on 2007-09-22
have you tried pommed?

---

### Post by diddledan on 2007-09-24
> 3) Start up from the Mac DVDs. Use Disk Utility (on the Utilities menu) to repartition the hard drive, leaving free space. I made lots of space for later installations.

A more useful way of resizing the mac partition and freeing up space for your ubuntu and possible windows partitions are:

1) open a teminal from applications/utilities/terminal.app
2) type `diskutil resizeVolume` for explanation of how to use the resizeVolume command.
3) Run the resizeVolume to create two new partitions, one for windows and one for ubuntu. (if you don't want the windows partition, or you want two linux partitions instead, you can either omit the '"MS-DOS FAT32" Windows 72.8G' section or replace it with an equivelent linux section.)

eg.
    diskutil resizeVolume /dev/disk0s2 175G Linux Linux 50G "MS-DOS FAT32" Windows 72.8G

I used 72.8G on my box for the windows vista partition because I have a 320GB hard drive, which left me with 298.1GB after lowlevel formatting, and 297.8GB when the efi system partition is taken into consideration. to get a list of your current partition layout, run: diskutil list. do not do anything with /dev/disk1s1 as this is your EFI partition and necessary for successful booting (should be approx 200MB)

---

### Post by cyberdork33 on 2007-09-24
> **diddledan said:**
> do not do anything with /dev/disk1s1 as this is your EFI partition and necessary for successful booting (should be approx 200MB)

This partition is not required for booting. Several people have completely eliminated it from their system. (and even others have converted to a completely MBR disk). From what we have gathered, the EFI partition is for certain Apple updates so it may be worth keeping.

---

### Post by zAo on 2007-09-25
> 04:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)
Any change that you Airport works without ndiswrapper?

---

### Post by mojopikon on 2007-09-28
Hi!

Sound works for me on Gutsy on an Intel-Aluminium-iMac 20'', *but* with loooooow volume.
Curiously, the mixer shows two sound devices:

- REALTEK ALC885
- HDA Intel

anyway, I can only hear a whisper.

Could anybody give me some clues? :-|

Thanks in advance

(and, of course, sorry for my bad english) :-$

---

### Post by Hartimer on 2007-10-09
> **cyberdork33 said:**
> Also for those that want to triple boot, it is best to install grub to the linux boot partition instead of the MBR as stated elsewhere.

How you do this?

I've tried 1001 things and was not able to do this so far :S neither with grub or lilo

---

### Post by cyberdork33 on 2007-10-09
> **Hartimer said:**
> How you do this?

I've tried 1001 things and was not able to do this so far :S neither with grub or lilo

At the end of your Ubuntu install, there is a button that says "Advanced". When you click that you can enter the specific partition you want to install grub to. If you already installed grub to the MBR, then you have to replace it with windows 'fixmbr' or otherwise.

If you have Ubuntu installed already you can install Grub to the partition from the command line. [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

