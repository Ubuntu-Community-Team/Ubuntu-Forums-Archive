---
title: "Here's a Real Challenge."
date: 2009-04-30
forum: Apple Hardware Users
---

### Post by ron3090 on 2009-04-30
Alright, I've got an original G3 iMac (Tray-loading) with the latest version of Debian installed. I installed debian erroneously, thinking it would run faster than 10.4. Silly me. Now, in an attempt to fix this, I am trying to install OS 9 or 10.2. I have both of the install CDs, but here's the problem: I think my CD drive is bad. When I try and boot from a CD or use a CD at all, it  1) is not detected and 2) makes a clicking noise repeatedly, as if the laser is trying to move but has a bad motor.

     Is there any way to boot from ANYTHING else, such as a USB stick? I tried using a USB drive, but it doesn't work before startup. I also have no Firewire ports.

HELP!!!

---

### Post by stream303 on 2009-05-01
Hmm.. how about a network install of Ubuntu via TFTPD with another machine, common for when you don't have a cd drive.

I have never done this personally, but there seems to be a lot of info out there for ubuntu tftpd installs, although the details of the tutorials seems to change a little bit depending on the version.

And I'm not sure if this would work for OSX - maybe someone can chime in...

---

### Post by tiresia on 2009-05-01
Can you start from debian and read a CD - I mean, is the CD-ROM totally broken or you can use it in Debian? Do you have a second Mac?

---

### Post by ron3090 on 2009-05-01
@tiresia: I cannot read CDs even in  Debian,so this led me to believe the drive was broken. I do have two other macs and a Xubuntu machine. so there are plenty of other options if I need to hook it up to something. I tried using an external CD drive, but for some reason, Debian doesn't accept any CDs from it. It detects the drive is there, but whenever I try to access the CD inside, it mysteriously unmounts itself for a few seconds, and says there's nothing in the drive.

@stream: Mac does have "Target disk mode," which is sort of like that, but to use it I need a firewire port on the iMac.

I've been searching around for answers, and I found one site that mentioned changing the firmware so that pressing the C key at startup would point to an external CD drive. Since my computer did not seem to detect the drive, I tried inserting a USB stick. The computer recognized it! Now all I need to know is if I can make a bootable USB stick with OS9 on it.

---

### Post by tiresia on 2009-05-01
> **ron3090 said:**
> Now all I need to know is if I can make a bootable USB stick with OS9 on it.

1. make an image (.dmg compressed) of the mac os 9 installer cd with the Apple disk Utility (on another Mac)
2. Insert the USB Stick and Restore the .dmg image on it with the Apple Disk Utility
3. Insert the USB Stick in the iMac and install it

(the same you can do with MacOSX - but you need at least a 4GB or bigger USB Stick)

----
Of course, you can install also Ubuntu starting from the USB stick

---

### Post by stream303 on 2009-05-01
Yep - holding down the "C" key is the key, unless the drive is truly broken. :)

Just to make sure - you are burning that iso image as an iso, and not just copying files over - AND burning at a very low rate that the older cdrom drive can handle right - like 1x, 2x or 4x on CD-R media?

Hold down the "C" key long enough to ensure that it is truly booting from it.

Some have had success by holding down the "C" key, and keeping it held down, PRIOR to turning on the power, and others do the opposite - turn on the power, and then pretty quickly hold down the "C" key - again long enough to ensure that it is booting.

Just thought I'd throw these out just in case it is a timing or media issue, rather than a truly broken drive....

---

### Post by tiresia on 2009-05-01
> **tiresia said:**
> 1. mac a image (.dmg compressed) of the mac os 9 installer cd with the Apple disk Utility (on another Mac)
2. Insert the USB Stick and Restore the .dmg image on it with the Apple Disk Utility
3. Insert the USB Stick in the iMac and install it

(the same you can do with MacOSX - but you need at least a 4GB or bigger USB Stick)
----
Of course, you can install also Ubuntu starting from the USB stick

Sorry, I forgot to mention, that BEFORE restoring the MacOS9 Installer on the USB Stick, you should format the USB stick as HFS+ (not journaled) INSTALLING ALSO THE DRIVERS FOR OS9 - otherwise the usb stick is not BOOTABLE!

---

### Post by stream303 on 2009-05-01
Another note about reviving OSX - do you have the real original restore disks *particular to that machine* or a retail version?

The reason I mention this is that some resellers or give-away machines offer up OSX disks that won't actually work on your box because the restore disks are particular to a specific model.

In addition, some who have tried to restore OSX try to use a version that is OLDER than what was originally released with that model - and the machine will detect this and refuse to install - so "downgrading" to a release prior to what was available when the machine was originally manufactured won't work.

No such problem with Linux!

---

### Post by ron3090 on 2009-05-01
> **tiresia said:**
> 1. mac a image (.dmg compressed) of the mac os 9 installer cd with the Apple disk Utility (on another Mac)
2. Insert the USB Stick and Restore the .dmg image on it with the Apple Disk Utility
3. Insert the USB Stick in the iMac and install it

(the same you can do with MacOSX - but you need at least a 4GB or bigger USB Stick)

----
Of course, you can install also Ubuntu starting from the USB stick

Ah, that's what I needed!

No, the CD drive is BROKEN. The motor that runs the lens is bad, I think, since I can hear it trying to spin up, but then failing multiple times with any CD.

I'll try that, tiresia, then report how it goes.

---

### Post by ron3090 on 2009-05-02
Well, surprise surprise, it didn't work.

I followed your instructions, and it worked fine until it came to my part. I (assumed) I set the device alias "cd" to the usb drive, but when I typed "boot cd," it came up with something like "can't OPEN cd." Restarting it and holding C did no good, becuse the firmware reset itself.

Now, in the device list, the drive is only listed as "device@2." The root of the problem here seems to be that it doesn't recognize the USB as a drive, just as "something's plugged in there."

Well, I'm clueless. What now? Can I hook up two systems over USB  or a network cable? I really don't know.

---

### Post by tiresia on 2009-05-02
1. Did you format the USB Stick as said as HFS+ installing also MacOS9 Drives?
2. Please, reset the PRAM (press ctrl-alt-P-R at boot up) and check if the Open Firmware detect the USB Stick just pressing the Opt-Key

---

