---
title: "Configure Yaboot to be used on another PPC Mac ?"
date: 2016-08-28
forum: Apple Hardware Users
---

### Post by panda-striling on 2016-08-28
Hi,
I have an iMac G5 17" with a dead SuperDrive, and I want to install Ubuntu on it.
I also have a PowerMac G5, which is the way I want to install Ubuntu on the iMac.
What I thought would work is:
-Put the iMac HDD on the PowerMac
-Install Ubuntu on the HDD using the PowerMac
-Put back the HDD on the iMac
-The iMac boot with Ubuntu installed and work
I didn't think about the driver issue because they have petty much the same hardware
iMac: G5 2,0GHz - ATi Radeon 9600 128Mb - 2GB RAM DDR
PowerMac: Dual G5 1,8GHz - ATi Radeon 9600XT 128Mb - 2GB RAM DDR
But, the problem is when I try to boot the iMac with the HDD, it doesn't work: Yaboot appear, but just after that (Second stage bootstrap), I got the question mark folder (in a little square in the middle of the screen, the rest of the screen is still yaboot menu with "l to boot to GNU/Linux, c to boot to the CD)
I read that it's because at the installation, Ubuntu configure yaboot to "work" with the machine it is installed on, and the problem is about the Open Firmware HDD path which isn't correct when swapping the HDD
I tried to replace the boot=*open firmware path* to boot=/dev/sda2 (which should be the Yaboot partition) in the /ect/yaboot.conf file but it still doesn't work (I put back the hdd on the PM), it's still boot on the PowerMac with issue, but still the same problem on the iMac
Is there anyway to install Ubuntu on this iMac G5 using another PPC Mac ? (because the Superdrive isn't working, so I couldn't boot to the Ubuntu DVD, and I won't buy any part for this iMac I found in the street (just haven't got the RAM, after putting 2x1Gb Stick, and Installing OS X with Target Disk Mode, it worked fine on Tiger)
All I actually have is the iMac G5 with no actual OS, the PowerMac G5 with no actual OS or HDD, the Ubuntu 12.04 LTS install DVD, and my MacBook Pro running Mavericks (which i'm using to type this message)
Thanks ^^

---

### Post by Fire_Chief on 2016-08-30
Hi Panda,

This article may be of help to you. It deals with booting the iMac from a USB drive after creating the bootable USB stick. Mavericks has the dd utility available from the Terminal.

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F")

Here's how to create the Ubuntu bootable USB stick using tools in OS X.
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick#Manual_Approach]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick#Manual_Approach")

Cheers!

---

### Post by panda-striling on 2016-08-30
You could boot a PowerPC Mac from USB ?
I had lot of PowerPC Mac (iMac G5, PowerMac G5, iBook G4, Mac Mini G4, PowerBook G4) and I never managed to boot a PowerPC Mac from USB, either with Linux or OS X.
It works on the MacIntel, but not on PowerPC.
I thought It would work because with OS X, you could swap your hard drive to an another Mac, and it would work without any problem (If the Mac is compatible with the OS X) and, it's the same for Ubuntu on classical PC.
But, anyway, I will give it a try.
Thanks for your reply ^^

---

### Post by Fire_Chief on 2016-08-31
It has more to do with the version of OpenFirmware that comes on the system. The revA iMac G5's don't support it apparently but some later revs seem to have the ability.

---

### Post by panda-striling on 2016-09-03
I have a Rev B iMac (the one with the Ambiant Light Sensors) :/

---

### Post by gsahli on 2016-09-04
Sorry if I'm too late to help.
I think you should try using Target Disk mode again, with the ubuntu install DVD in the target mode computer.

---

