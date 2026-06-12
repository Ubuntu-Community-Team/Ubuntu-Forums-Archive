---
title: "Ubuntu 18.10 installer bug? (doesn't see SSD partitions)"
date: 2018-12-04
forum: Apple Hardware Users
---

### Post by dsolaris on 2018-12-04
[IMG]https://i.imgur.com/cv2ftW2.png[/IMG]

I have Ubuntu 16.04 on my Mac Mini.

Decided to go 18.10 and install it on the second SDD on which i have Win 10 and a couple of partitions.

Well the installer for some reason can't see these partitions. They were made on Windows using built in partition manager.

One important thing to add, Windows partition is not hibernated. I did the powercfg thing earlier and in fact you can see on the right side of the screenshot there is no hibernate file on the partition which by the way is successfully mounted. Which brings us to the second topic.

As you can see i was able to mount the Windows partition (after installed failed to see it). And fdisk was able to see all of the partitions on that disk, as we can see on the second terminal.

So the problem is definitely in the installer.

Any clues are welcome.


Computer specs:
Mac Mini Late 2012 with two internal drives
SSD 1: OSX and Ubuntu 16.04
SSD 2: Windows 10 and *<trying to install Ubuntu 18.10 *:cool:*>*

---

### Post by oldfred on 2018-12-04
Moved to Apple hardware sub-forum where users with a Mac may be able to help.

I thought Mac were all UEFI now, you are showing BIOS/MBR install of Windows on your other drive.


Some older threads, which may help, but do not know Mac.
       [SOLVED] Video performance of Ubuntu 16.04 on 2007 Mac Mini 2,1 (Intel Integrated 945GM/GMS)
[https://ubuntuforums.org/showthread.php?t=2349732](https://ubuntuforums.org/showthread.php?t=2349732)
Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)
Mac Mini 
[http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/)
[http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind](http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind)
[http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890](http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by dsolaris on 2018-12-04
Thank you!

And we can close the case as SOLVED!

Don't want to point my finger at Microsoft, but the fact of the matter is, i originally made this this disk GPT yet the Windows 10 installation complained it can't be installed there so i had to remove it and go with the MBR. Because i thought maybe it's because it's an old mac.

---

### Post by oldfred on 2018-12-04
It is how you boot install media, both Windows & Ubuntu. If you boot in UEFI mode it will install in UEFI mode and if you boot in BIOS mode it will install in BIOS mode.
Windows only installs in UEFI mode to gpt partitioned drives and only in BIOS mode to MBR(msdos) partitioned drives.
And if you force a BIOS Windows install to a gpt drive, it incorrectly converts from gpt to MBR, leaving the backup gpt partition table.
The Linux drivers see both MBR & gpt and only offer to totally reconfigure drive.

---

