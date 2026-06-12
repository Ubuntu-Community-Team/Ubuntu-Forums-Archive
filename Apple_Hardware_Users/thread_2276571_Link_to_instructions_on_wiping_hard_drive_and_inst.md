---
title: "Link to instructions on wiping hard drive and installing ONLY Ubuntu on Mac Book Pro?"
date: 2015-05-03
forum: Apple Hardware Users
---

### Post by tim112 on 2015-05-03
:guitar:
Hi Folks.   

[INDENT]I'm currently have a Mac Book pro that I bought used. I found out (later after I purchased from a pawn shop that I work at) that I need to wipe the hard drive and either reinstall Apples OS or wipe clean and install Linux. I want to do the latter, but before I do I want to make sure it's feasible and possible. Can anyone point me to a link on how to do so with a USB Stick? I ask this because the DVD drive isn't working, but I also do have a USB portable drive I can use to do the install if necessary. 

What I want to do is totally wipe the drive / format and then install ubuntu so that I may develop with it in using PHP, SQL Lite, etc, for some CMS work and some PHP work at home. (So anyone that wants to chime in and help with that or links to the same would be great). 

Again, this thing only has a bad DVD drive so I'll have to install using a USB stick, but I'd think that should not be a problem? 

Any help would be greatly appreciated. [/INDENT]

Regards
Tim

---

### Post by este.el.paz on 2015-05-07
@Tim:

The general wisdom and my own experience is to keep OSX and either do a dual-boot set-up, OR use Parallels, VMFusionware, or VirtualBox to run linux OSs.  Possibly you might need rEFInd depending on what model Mac you have, so that you can boot OSX and non-OSX . . . search the web for "rodbooks."

In terms of USB boot, actually the PowerPCFAQ on the Ubuntu wiki has detailed instruction on how to boot from USB . . . or the Apple Discussion group would likely have instructions for how to create a bootable USB drive using Disk Utility . . . which of course means you have to have OSX installed . . . .  In linux it seems like "mkusb" is a utility that can "make a usb boot drive" . . . which of course means you need linux installed . . . somewhere.

Read the "Mactel" wiki in the sticky's of this sub-forum to get some idea of what things might need attention when running linux on an Apple . . . such as the "fan control" threads . . . .

e...

---

### Post by tim112 on 2015-05-09
Thank you so much. I'll check it out.. I think I'm going to use a PC box first and then later install on Mac. I will eventually install on all of my hardware. I really like ubuntu a lot. Can't say enough about it.. Thanks again.
Tim

---

### Post by William_H._Jones_I on 2015-05-14
tim112, I just saw a YouTube video where the user performed a dual-boot setup of Mac OS X and Ubuntu where rEFIt/rEFInd was not needed.  All he did was make a Ubuntu boot thumb drive, restart his Mac, use the Option key at the chime to select the thumb drive (it was called EFI boot, IIRC), then proceed to load Ubuntu as normal.  Once the instal was done, he only had to use the Option key to select the OS of choice.   Here's the link

[https://www.youtube.com/watch?v=Sl_5AV4twyo](https://www.youtube.com/watch?v=Sl_5AV4twyo)

---

### Post by William_H._Jones_I on 2015-05-15
Well, it didn't work.  I was able to boot off either the thumb drive or the install DVD, but no joy.  My boot options, after installing rEFInd, were:

Boot EFI\boot\grubx64.efi from 2MiB FAT volume
Boot Fallback boot loader from 2 MiB FAT volume
Boot Legacy OS from whole disk volume

I chose the first one, then chose the option to get the "live" version, but got a screen with the following:

[          6.284951] i8042: No controller found
[          6.437676] ACPI PCC probe failed.
starting version 219

That stayed on the screen for a few minutes, then it went black.  I waited for a while, but it never went any further than that.  Prior to that, I got an error message stating that '/boot/' was not found  it seems as if Apple has really gone out of their way to make dual-booting extremely difficult.  Apparently, Microsoft is also pushing their computer manufacturer partners in the same direction.  This is really frustrating for me, as I have tried all sorts of methods, none of which have been successful.

---

