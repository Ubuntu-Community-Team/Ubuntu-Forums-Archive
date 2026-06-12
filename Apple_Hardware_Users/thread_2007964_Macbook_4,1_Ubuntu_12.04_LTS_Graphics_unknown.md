---
title: "Macbook 4,1 Ubuntu 12.04 LTS Graphics unknown"
date: 2012-06-21
forum: Apple Hardware Users
---

### Post by Quenepas on 2012-06-21
Hello, Im new here and to Linux as well so I'll try to be as specific as I can. Any type of help is greatly appreciated :).

Just followed [this guide]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required") to triple boot OSX, Win7 and Ubuntu. Since I already had Bootcam with Windows, the guide asked me to create 2 additional partitions, 1 for Linux and 1 for Linux Swap. During installation it seems like the swap file needed was just about 1.5GB HDD space. Ubuntu Disk Utility shows 5 partitions (in order),

EFI System Partition 210MB FAT32
OSX 254GB HFS+
"Linux" (as renamed during OSX format) 51GB FAT32 /dev/sda3 not mounted
Linux 51GB FAT32 ext4 v1.0 Mounted at L
Swap Space 1.6GB /dev/sda6
and finally...
BOOTCAMP 141GB

Ubuntu seems to work, OSX seems to work and Windows doesnt seem to boot thru rEFIt... boots back to Ubuntu :/ before booting it comes up with GNU menu (which I dont know). 

So afaik My problems are:

1) Windows 7 wont boot thru rEFIt.

When choosing Windows Vista (dunno why, I have Win7) Windows boot Manager gives error: File \boot\BCD Status:0xc0000225 Info An error ocurred while attempting to read the boot configuration data. Enter=continue ESC=Exit. I press continue and it does nothing. It asks for the installation disc and attempt a repair but I dont think this would be solved that easily.

Checking Disk Utility on OSX shows 8 partitions including osx... this doesnt look good :/

2) When Ubuntu start it rapidly tell about an internal error : "/usr/share/apport/apport-gpu-error-intel.py"

3) the graphic card seems to be unknown within Ubuntu.

I have a black Macbook... Thanks for your time!! ):P

---

### Post by hectorviov on 2012-08-23
I decided to remove all partitions and just keep Ubuntu. But I have the problem with the graphics unknown thing. Where can I get the driver? Also the touch pad seems to be hard, I have to press my finger hardly to get it to move, this didn't happened on windows or mac.

---

### Post by piperbarb on 2012-08-24
I, too, have a (black) Macbook 4,1.  I have it dual-booting Ubuntu 64-bit 12.04 and OS X 10.7.4.  I have had no problems with the video.  The only tweak I had to do was get the iSight Webcam working.  I did do a clean install of Ubuntu.  That might make a difference.   I never bothered to install Windows on my Macbook.  Ubuntu works seamlessly along.  The OS X/Ubuntu dual boot is the perfect match.

---

