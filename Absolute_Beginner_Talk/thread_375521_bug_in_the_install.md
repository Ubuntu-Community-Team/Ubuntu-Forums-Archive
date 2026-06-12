---
title: "bug in the install"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by ajor on 2007-03-03
Hello!
I've got a laptop with Windows XP running on it.
I've downloaded Ubuntu (6.10-desktop-I386) on my computer, I've done the Winmd5sum check and created a new disk from the .iso
I tried to start this disk from Windows, but it didn't work. Then I restarted my computer and booted from the CD, I arrived on the Ubuntu menu and pressed "Start or install Ubuntu", nothing happened, I just had a green "loading" message on top and the CD seemed to turn quite quickly, but nothing happened. I had to shut down the computer. I tried three times, it always does the same. What's going on? Did I forget anything?

Thanks a lot for helping me.

---

### Post by esaym on 2007-03-03
What are the laptop specs?  What is the model number?

---

### Post by jpkotta on 2007-03-03
> **ajor said:**
> Hello!
I've got a laptop with Windows XP running on it.
I've downloaded Ubuntu (6.10-desktop-I386) on my computer, I've done the Winmd5sum check and created a new disk from the .iso
I tried to start this disk from Windows, but it didn't work. Then I restarted my computer and booted from the CD, I arrived on the Ubuntu menu and pressed "Start or install Ubuntu", nothing happened, I just had a green "loading" message on top and the CD seemed to turn quite quickly, but nothing happened. I had to shut down the computer. I tried three times, it always does the same. What's going on? Did I forget anything?

Thanks a lot for helping me.

Try using the "check disk for errors" option on the menu when the disk boots.  It does the md5sum just like you did before, but will catch any errors that occurred while burning.  But, that will probably not yield any errors since you did the md5sum before.

The fact that the menu comes up means you did everything right.  I can't think of why it's doing what it's doing, other than a burn error.

---

### Post by ajor on 2007-03-03
To Esaym: I don't know what you mean by "model number". What I can say is that the brand is "Hundyx", you can have a look at it here (in spanish, sorry...): [http://www.appinformatica.com/fichas/portatiles/031app12599.htm]("http://www.appinformatica.com/fichas/portatiles/031app12599.htm")
or here: [http://www.hundyx.net/Producto/M665Se.htm]("http://www.hundyx.net/Producto/M665Se.htm")

Moreover, here are the informations given by Everest:

> Motherboard	
CPU Type	Mobile Intel Yonah, 1466 MHz (11 x 133)
Motherboard Name	VIA VN800
Motherboard Chipset	Unknown
System Memory	448 MB
BIOS Type	Phoenix (09/27/06)
	
Display	
Video Adapter	VIA/S3G UniChrome Pro IGP  (64 MB)
Video Adapter	VIA/S3G UniChrome Pro IGP  (64 MB)
Monitor	Plug and Play Monitor
	
Multimedia	
Audio Adapter	VIA AC'97 Enhanced Audio Controller
	
Storage	
IDE Controller	VIA Bus Master IDE Controller - 0571
IDE Controller	VIA Serial ATA Controller - 3149
SCSI/RAID Controller	ENE PCI Memory Stick Card Reader Controller
SCSI/RAID Controller	ENE PCI Secure Digital / MMC Card Reader Controller
Disk Drive	FUJITSU MHV2080AH  (80 GB, 5400 RPM, Ultra-ATA/100)
Disk Drive	SEAGATE ST3160212A USB Device  (149 GB, USB)
Optical Drive	MATSHITA DVD-RAM UJ-850S
SMART Hard Disks Status	OK
	
Partitions	
C: (NTFS)	39997 MB (33203 MB free)
D: (NTFS)	36310 MB (36154 MB free)
F: (FAT32)	152588 MB (1223 MB free)
Total Size	223.5 GB (68.9 GB free)
	
Input	
Keyboard	Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse	PS/2 Compatible Mouse
	
Network	
Network Adapter	VIA Rhine II Fast Ethernet Adapter  (192.168.2.2)
	
Peripherals	
USB1 Controller	VIA VT83C572 PCI-USB Controller
USB1 Controller	VIA VT83C572 PCI-USB Controller
USB1 Controller	VIA VT83C572 PCI-USB Controller
USB1 Controller	VIA VT83C572 PCI-USB Controller
USB2 Controller	VIA USB 2.0 Enhanced Host Controller
USB Device	USB Mass Storage Device
Battery	Microsoft AC Adapter
Battery	Microsoft ACPI-Compliant Control Method Battery
	
Problems & Suggestions	
Problem	Disk free space is only 1% on drive F:.

To Jpkotta: is it normal that Ubuntu doesn't want to start from Windows either? I started it from the .iso and not from the cd (which would mean that the error isn't a burn error)

---

### Post by 3rdalbum on 2007-03-03
> **ajor said:**
> 
To Jpkotta: is it normal that Ubuntu doesn't want to start from Windows either? I started it from the .iso and not from the cd (which would mean that the error isn't a burn error)

That's completely normal - Ubuntu is an operating system, so it does not start from within another operating system.

I believe there's a key that you can press at the first Ubuntu menu that shows you special options you can add to make Ubuntu boot on uncooperative machines. I think it's F1. That will show you the things you can try.

---

### Post by esaym on 2007-03-04
The model number is M665SE.  And searching google gives me no results for running linux on that laptop.  It would appear that you are the first one in the world to try linux on this model laptop..  I am not sure where to start with a problem like that...

---

### Post by ajor on 2007-03-04
Well... I feel quite happy about that...
I tried the "memory test" which is in the menu of Ubuntu but it's rather weird since the test never ends, it seems like it's running again and again and never stop. 
I tries to run the "grafics safe mode" but it's doing more or less the same (I mean about nothing), I tried also the "check cd defects" but nothing happened.

Are there any computer that aren't compatible with Linux? If so, I'm not lucky...
Appart Ubuntu, are there any other version of Linux (Mandrake, Debian, etc) that I could try? or is it going to do the same?

---

### Post by esaym on 2007-03-04
> **ajor said:**
> Well... I feel quite happy about that...
I tried the "memory test" which is in the menu of Ubuntu but it's rather weird since the test never ends, it seems like it's running again and again and never stop. 
I tries to run the "grafics safe mode" but it's doing more or less the same (I mean about nothing), I tried also the "check cd defects" but nothing happened.

Are there any computer that aren't compatible with Linux? If so, I'm not lucky...
Appart Ubuntu, are there any other version of Linux (Mandrake, Debian, etc) that I could try? or is it going to do the same?

memtest repeats itself yes.  What do you mean when you checked the cd for defects nothing happened?  Do you mean no errors were found or that the test would not run?

There are all kinds of ubuntu version.  I like Kubuntu.

Version 6.06:
[http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/kubuntu-6.06.1-desktop-i386.iso](http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/kubuntu-6.06.1-desktop-i386.iso)

Version 6.10:
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/kubuntu/edgy/kubuntu-6.10-desktop-i386.iso](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/kubuntu/edgy/kubuntu-6.10-desktop-i386.iso)

Version 7.04:
[http://cdimage.ubuntu.com/kubuntu/releases/feisty/herd-5/feisty-desktop-i386.iso](http://cdimage.ubuntu.com/kubuntu/releases/feisty/herd-5/feisty-desktop-i386.iso)

---

### Post by ajor on 2007-03-04
I mean the test didn't run, the computer just does like it did when I pressed "Install Ubuntu", it blocks itself (sorry about my dodgy english...)

Don't you think I would have the same kind of problems with Kubuntu or something else?

---

### Post by igknighted on 2007-03-04
Try hitting F6 before you do anything and add the following to the line of text that appears:
"noapic nolapic" (without the quotes)

---

### Post by Rajith on 2007-03-05
Did u partition the hard disk for linux.....
Linux wont run on windows partition....

---

### Post by ajor on 2007-03-05
I've just tried the noapic thing but I get the same problem: a  little "loading" green message on top, the disc running and nothing else...

---

### Post by ajor on 2007-03-05
I've got two partitions (40 gigas each), one with windows installed on it, and a clean one ready to be used by linux. I formated the linux partition, so it should be allright...

---

### Post by esaym on 2007-03-05
> **ajor said:**
> I mean the test didn't run, the computer just does like it did when I pressed "Install Ubuntu", it blocks itself (sorry about my dodgy english...)

Don't you think I would have the same kind of problems with Kubuntu or something else?

That sounds weird.  The test should always run.  Perhaps the cd you made it bad?  Try burning another one or try one of the kubuntu cds I posted.

---

### Post by aerie on 2007-03-05
Hi, do you have any usb device connected to the computer when installing? I could't even start the live cd due to a memory card reader connected to the mainboard. I disconnected it and managed to install ubuntu. I've seen problems with external usb hard disks too.


When the live cd starts up press F2 choose your language and then F6 and delete the "quiet-splash" ending (only this), then type in "break=bottom" and press Enter. This way you will see where it fails and may be it will give you a clue for further searching in the forum.

---

### Post by ajor on 2007-03-05
I tried the breakbottom thing but I get the same problem.
Then I burned a new disc , but I've got exactly the same trouble. 

That's a weird story, isn't?

---

### Post by aerie on 2007-03-06
if you bought your computer in appinformatica you may be spanish y estamos haciendo el tonto los dos:) . Can you take a photo of the screen when it freezes and post it?. You said that you tried typing break=bottom but, have you tried installing ubuntu without the usb hard disk?

---

### Post by ajor on 2007-03-06
*Que putada este ordenador...*

I've tried installing Ubuntu without any USB device and I obtain the same thing (with braek=bottom or noapic nolapic).
I haven't any camera but the screen that I obtain is exactly the same as the menu, there is just a little "loading" green message on top (which is duplicated in the left top corner)

---

### Post by aerie on 2007-03-07
have you tried the safe mode I think it's F3

---

### Post by ajor on 2007-03-07
Yes I did. No way to make this cd working... I guess the problem comes from a configuration of my computer... At the moment I'm looking for another Linux distribution to try on it, do you know which one would be the best in my case ? Mandrake?

---

### Post by igknighted on 2007-03-07
Ewww... not mandriva.  I would say look at: Opensuse, Knoppix, and guess as a third choice perhaps either Mandriva or PC Linux OS

EDIT: I say that with jest about mandriva... the newest version 2007 is pretty good, their best in a while.

---

