---
title: "Scanner always stops after a few weeks"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2006-07-13
I'm riding an old unanswered topic, but this is driving me NUTS:evil: 

My scanner always work with every new release of Ubuntu/Kubuntu. Then after two weeks or so, its al of a sudden I get the " Snapscan Device not found" thingy. And that always happens no matter what release I used. But it only works for a while from a FRESH install and then adding Xsane with synaptic gets it going if it was not included in the package.

With Dapper, I was extremely careful to make sure that I don't install things that might conflict with Sane. Everything worked perfectly, then one day, afer a week or so of NO new apps installed, gone is the scanner.

Now the Sane website is absolutely useless, cause none of what they say is like that for Ubuntu. (Even the directory structure is different.)

The command "sane-find-scanner" shows my scanner in place. Command "scanimage-L" also show my scanner is there. Command "lsusb" also show my scanner. Even "cat /etc/****" (sorry can't recall the complete command offhand) also show my scanner. But there the "device=none" which should not be like that according to the sane manpage.

Trying to scan as root does not work. Unplugging the scanner, rebooting then run above commands, scanner is gone. (That's expected.) Next shut down, plug scanner back, reboot, and the commands show my scanner returned as above, but still don't work.

Command "sudo rmmod scanner" nothing happens. "sudo modprobe scanner" returns with "module scanner not found, and yes I tried to add the vendor type etc. afterwards as well.

I choose 'completely remove' all things to do with sane from synaptic. It removes xsane, libsane and what else. Reboot, just to double check. Re-installed xsane, libsane only. Nothing. Add sane, still nothing, and so I can go on and on. 

Oh and the sane.d/scanner.config is the only config files that I can find, and my scanner is definitely there. For the fun I added my scanner manually, reboot, but still nothing.

For those willing to try and help, I have an Acer 3300U on a USB port. It sits in my case on libscan:004:002. If I am back at my box tonight, I could post the output of what I have.

Regards

---

### Post by bohboh on 2006-07-13
I dont even own a scanner so cant help, but a quick search turned up this which you may have already tried.

[http://snapscan.sourceforge.net/#work](http://snapscan.sourceforge.net/#work)

HTH

---

### Post by GrootBrak on 2006-07-13
Thanx been there. Offhand I can't recall which of the below matches mine, but I think its the former. I tried to download it via internet, but can't find a decent link. All sites is trying to get me registered or pay before I download. I've read that the files should be on the CD that came with it. I will try that as well. But then again, why was it working and then stopped just like that? I've read similair posts where a scanner simply stops after working perfectly for a few weeks.


Anyone know of a free place to download these files?
> u176v046.bin
u222v067.bin

Regards

---

### Post by bohboh on 2006-07-13
I found this:

> You need to check if your particular model is supported under linux. Checkout the device table on the SnapScan Website and make a note of the USB-ID and Firmware file for your device. You will need to source the firmware file for your scanner - I found mine (u176v046.bin) lurking in a CAB file on the Windows driver CD that came with the scanner.

So chances are the other bin file may be there also.

FYI:
[http://bsdbox.homeunix.com/modules.php?op=modload&name=Sections&file=index&req=printpage&artid=19](http://bsdbox.homeunix.com/modules.php?op=modload&name=Sections&file=index&req=printpage&artid=19)

---

### Post by GrootBrak on 2006-07-16
I've added the .bin file, but now trying to access xsane shows the there is no scanner available, same for Kooka.](*,) 

Here is output from etc/sane.d/scanner.config

> # Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
# OLD path after# #firmware /usr/share/sane/snapscan/your-firmwarefile.bin
firmware /etc/sane.d/u222v067.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb
#/dev/bus/usb/002/004 bus=usb
 The rest is as is. I tried adding /dev/bus**** line, but that came out blank.

Before I added the firmware line, lsusb, scanimage -L both showed my scanner. Now its gone. Removing the line and rebooting, then the above commands show the scanner again.:confused: 

I hope that I can get help with this problem and have scoured google for answers, but none so far. It seems that I will have to either re-install my system or re-compile my kernel. The latter I am not willing to try in case I bugger up things.
Regards

---

### Post by bohboh on 2006-07-17
Sorry, i dont even own a scanner to be able to help. My usb goodies (printers,etc) just seem to work.

Must be others that do have scanners which can advise. Anyone?

Good luck. :)

---

### Post by laapata on 2006-08-10
i have the same scanner and had the same problem. it can be solved by copying the firmware to the harddrive and then make a link in snapscan.conf. i am a noob and dont remeber the full instructions, however for dapper here is what i did

copy the firmware from ur windows driver. for MiraScan driver (which i got) its in a folder named "Bin" and it is called u176v046.bin.

using root/sudo copy this to /etc/sane.d/

do that the path for this becomes /etc/sane.d/u176v046.bin

to use root in GUI on the desktop press Alt + F2 to open run command window and type 

gksudo nautilus

use the explorer (nautilus) to find the firmware file and to copy it to the destination.

in the destination folder, ie /etc/sane.d/   there is a file called snapscan.conf

using root open it in a text editor. in the fourth/fiveth line it says

firmware .....some random path....

edit it to read 

firmware /etc/sane.d/u176v046

exit saving the changes

if ur scanner was on, turn it of and then on again, xsane should now work

NOTE to ubuntu developers, the firmware for 3300U is u176v046.bin NOT the one identified in the SANE manual (i think its u222v0xxx.bin)

---

