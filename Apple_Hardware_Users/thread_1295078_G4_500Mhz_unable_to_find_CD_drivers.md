---
title: "G4 500Mhz unable to find CD drivers"
date: 2009-10-19
forum: Apple Hardware Users
---

### Post by TheKLF99 on 2009-10-19
I bought an G4 500mhz Apple Mac a few months ago off eBay, it came with no Mac OS on it, and so I've decided to put Ubuntu on it.  

I just tried to put Ubuntu on it and it starts booting off the CD, then it gets to the detect and mount CD point and asks for a floppy disk with the driver on it.

I haven't got a floppy disk with the driver for the CD drive on it as the Mac is second hand and didn't come with any drivers.

I've opened the Mac up and the drive just appears to be a standard IDE drive which has me really confused as I normally use PC's and normally PC IDE drives automatically work with a generic driver.  

The only thing that is a bit strange about the CD is the way it goes into the drive, when the CD drive ejects it drops a flap and then the CD comes out of a little white caddy in the middle, I presume this is just a standard Mac CD drive?

I have also tried the option to manually mount the CD-Rom drive using both CDROM and NONE drivers, and again it just tells me it can't mount the drive, and I've gone into the CLI and in CLI also get told it can't mount the CD, I've also tried mounting the other drives like HDA,B,C,D, D1,D2,D3.... and the only response I get from them is the HDD drives come up with Input/Output error message.

Does anyone know what I'm doing wrong or where I need to go to find the drivers for the CD drive, at present I'm using the Ubuntu Alternate Install PPC disk, or is there a disk out there that I could boot off and install Ubuntu from the internet?

I have also got lots of other DVD drives lying around, these are all PC drives, would I be able to get it working with one of these, or does a PC IDE drive work totally different to a Mac IDE drive?  I've also got a self-built USB drive (a Plextor IDE drive in a USB enclosure) it works with my PC and my PC can boot off it, will the Apple Mac do the same if I plug it in, or is it not compatible?

---

### Post by kerry_s on 2009-10-19
:lolflag: apples are always a pain.
i'm just going to point you to the doc's & hope it helps.
[https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html)

---

### Post by oswaldkelso on 2009-10-19
> I bought an G4 500mhz Apple Mac a few months ago off eBay, it came with no Mac OS on it, and so I've decided to put Ubuntu on it.  

I just tried to put Ubuntu on it and it starts booting off the CD, then it gets to the detect and mount CD point and asks for a floppy disk with the driver on it.

I haven't got a floppy disk with the driver for the CD drive on it as the Mac is second hand and didn't come with any drivers.

I didn't think there was a floppy on that model. Maybe the CD is a dud. Make sure you have the correct disk (PPC) Just hold down the C key on boot. If that fails opt or alt key on boot is all I've ever done to boot a linux distro on PPC. With the alt or Debian net install all you should need is a good Ethernet internet connection. 

> 
I've opened the Mac up and the drive just appears to be a standard IDE drive which has me really confused as I normally use PC's and normally PC IDE drives automatically work with a generic driver.  

The only thing that is a bit strange about the CD is the way it goes into the drive, when the CD drive ejects it drops a flap and then the CD comes out of a little white caddy in the middle, I presume this is just a standard Mac CD drive?

Yes

> I have also tried the option to manually mount the CD-Rom drive using both CDROM and NONE drivers, and again it just tells me it can't mount the drive, and I've gone into the CLI and in CLI also get told it can't mount the CD, I've also tried mounting the other drives like HDA,B,C,D, D1,D2,D3.... and the only response I get from them is the HDD drives come up with Input/Output error message.

Does anyone know what I'm doing wrong or where I need to go to find the drivers for the CD drive, at present I'm using the Ubuntu Alternate Install PPC disk, or is there a disk out there that I could boot off and install Ubuntu from the internet?

Debian. see my imac how to in my sig for tips they are generally comparable with Ubuntu. but Ubuntu Alternate should work fine.

> I have also got lots of other DVD drives lying around, these are all PC drives, would I be able to get it working with one of these, or does a PC IDE drive work totally different to a Mac IDE drive?  I've also got a self-built USB drive (a Plextor IDE drive in a USB enclosure) it works with my PC and my PC can boot off it, will the Apple Mac do the same if I plug it in, or is it not compatible?

Yes they should work and yes but it requires much more work to boot ppc from usb. If you change the drives they are very picky as to the settings as in root slave etc. If you can work out the existing setting first from your old drives great. As a general rule the CD/DVD is master and ide drives CS. This is not hard and fast. 

I doubt there is anything wrong with your drives but you could change one to test.

---

### Post by oswaldkelso on 2009-10-19
ref: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

> Installer cannot detect CD-ROM

If the installer says "No common CD-ROM drive was detected" and asks for a driver floppy when istalling on a G4 Powerbook, answer no to "load from a driver floppy?", no to "Manually select a CD-ROM module and device?", and you will get a red screen with "Installation step failed". Hit "Continue". You will see the installer main menu. Press FN-option-F2 to bring up another console. Press Enter to activate the console. At the busybox prompt (~ #), enter:

```
modprobe ide-scsi
```

> then press Fn-option-F1 to get back to the installer main menu, and choose "Detect and mount CD-ROM". 

---

