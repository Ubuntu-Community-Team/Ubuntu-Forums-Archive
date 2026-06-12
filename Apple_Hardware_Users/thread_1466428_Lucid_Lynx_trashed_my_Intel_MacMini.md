---
title: "Lucid Lynx trashed my Intel MacMini"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Kiwiiano on 2010-04-30
G'day,
I attempted to install Lucid Lynx on an external USB drive on my Intel MacMini today. It took a bit of fiddling until I realised that nothing would happen unless I disconnected all the other volumes normally attached. Finally the ISO CD booted and the installation process fired up right to the point where I was offered the options of either erasing my HD & clean installing Ubuntu or only installing it on the largest contiguous space on the drive. 

I didn't want to trash OSX, so opted for the latter but it was declined as 'not enough room'. No option for external drives, or pen drives.....

OK, so shut down Ubuntu and go back to OSX, except that it appears the HD has been got at, even though supposedly I stalled the process before anything drastic was done. Any attempt to start the computer gets either to a sort-of command line announcement that "there is no bootable volume present, insert the disk and press any key." Any bootable volume such as a clone of my Mini drive on a USB ext HD or OSX Leopard installation discs fail to change anything. Booting in Target Disk Mode, Open Firmware, Single-User, or Verbose Mode all fail. Resetting the PRAM had no effect (almost as if it's not accessing the keyboard). The only response I can get is from the Ubuntu ISO, which launches apparently as normal but wants to erase my HD.

Heeeeelpp!!! Any Mac users with any suggestions out there? What on earth has Ubuntu done to the Mini?

---

### Post by devnuller on 2010-04-30
> **Kiwiiano said:**
> G'day,
I attempted to install Lucid Lynx on an external USB drive on my Intel MacMini today. It took a bit of fiddling until I realised that nothing would happen unless I disconnected all the other volumes normally attached. Finally the ISO CD booted and the installation process fired up right to the point where I was offered the options of either erasing my HD & clean installing Ubuntu or only installing it on the largest contiguous space on the drive. 

I didn't want to trash OSX, so opted for the latter but it was declined as 'not enough room'. No option for external drives, or pen drives.....

OK, so shut down Ubuntu and go back to OSX, except that it appears the HD has been got at, even though supposedly I stalled the process before anything drastic was done. Any attempt to start the computer gets either to a sort-of command line announcement that "there is no bootable volume present, insert the disk and press any key." Any bootable volume such as a clone of my Mini drive on a USB ext HD or OSX Leopard installation discs fail to change anything. Booting in Target Disk Mode, Open Firmware, Single-User, or Verbose Mode all fail. Resetting the PRAM had no effect (almost as if it's not accessing the keyboard). The only response I can get is from the Ubuntu ISO, which launches apparently as normal but wants to erase my HD.

Heeeeelpp!!! Any Mac users with any suggestions out there? What on earth has Ubuntu done to the Mini?

Can you be more specific with regard to the initial boot from CD? When you say you were offered options to erase/install, do you mean specifically erase/install the external drive? Can you be sure you chose the right hard drive? Have you tried holding down the alt key when booting the mini? You have a backup (disk clone or disk image) of your OS X instance?

---

### Post by 3rdalbum on 2010-04-30
> **Kiwiiano said:**
> G'day,
It took a bit of fiddling until I realised that nothing would happen unless I disconnected all the other volumes normally attached.

Sounds like you didn't plug them back in.

Oh and BTW you can't get to the Open Firmware prompt on an Intel Mac, it doesn't have Open Firmware.

---

### Post by Macchi on 2010-04-30
Excuse me but I believe that the free disk space for Linux installation on Macs should be prepared initially with bootcamp, such as in: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by devnuller on 2010-04-30
> **Macchi said:**
> Excuse me but I believe that the free disk space for Linux installation on Macs should be prepared initially with bootcamp, such as in: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I agree. Bootcamp is typically used to partition the internal hard drive to allow for OSX/Windoze dual-boot setups. I wouldn't imagine there would be any difference if the hard drive were external and or the "other OS" were not Windoze. The OSX master boot record (MBR) would still need to know there was another OS installed.

It sounds to me like the original poster has trashed his MBR. There may be ways to recover/rebuild it - there may be answers on the interweb.

Here we are, read this : [http://forums.macrumors.com/showthread.php?t=706055](http://forums.macrumors.com/showthread.php?t=706055)

---

### Post by Kiwiiano on 2010-04-30
Problem solved... sort of. I woke up this morning with the thought that maybe it was something to do with the keyboard????? in that none of the keyboard inputs for Target Disk Mode, zapping the PRAM etc had reacted. I swapped the little white Apple kybd for an old Bondi Blue model and had another try at TDM..... got it first try. Ran Disk Utility and Warrior more as an act of faith than anything....all clear. Restarted and got the Black screen of death "no bootable volume" again, restarted and reset the PRAM. This time it worked !! YAAAY!!

It is possible that all it needed was to cool down overnight. The suspect keyboard worked OK on this MBP and appears to be just fine with the Mini. I guess we'll never know for sure.

Re the queries about the Installation DVD, it is a standard Leopard Intel-only Installer. The Ext HD backup disk is identified by the Startup Disk Preference as an option so it should be bootable. But if the PRAM had been messed with maybe they weren't accessible. ??????

Thanks for your suggestions

~Kiwiiano

---

### Post by Macchi on 2010-05-01
Great that you found a solution for the problem!

NOW as a courtesy you may tag the thread as [SOLVED]

---

