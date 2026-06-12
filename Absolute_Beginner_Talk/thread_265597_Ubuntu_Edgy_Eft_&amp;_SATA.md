---
title: "Ubuntu Edgy Eft &amp; SATA"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by joanartur on 2006-09-26
Hello world !
I am happy to meet such a great community like this.

Does someone know, if the new "Ubuntu Edgy Eft" version will be compatible with "serial-ata" (sata) hard drives ?

I can't wait to install Ubuntu in my new laptop !
But sadly I have not found any Ubuntu version compatible with my laptop's serial-ata hard drive :-k 

Thank you very much !

---

### Post by Paulus on 2006-09-26
personally I have been able to install it on my SATA2 drive with no problems whatsoever..  your best bet I would have thought it to simply try it out- if the live CD detects you drive properly then I can't see any reason why it wouldnt' work.

---

### Post by megamania on 2006-09-26
> **joanartur said:**
> Does someone know, if the new "Ubuntu Edgy Eft" version will be compatible with "serial-ata" (sata) hard drives ?

I can't wait to install Ubuntu in my new laptop !
But sadly I have not found any Ubuntu version compatible with my laptop's serial-ata hard drive :-k 


Ubuntu is already compatible with SATA drives, but maybe not with all of them. I have been using ubuntu with my sata hard disk since april 2005 with no problems.

You should provide more info regarding your system.

---

### Post by Kabal on 2006-09-26
Well I've got SATA drives and PATA drives and I never got Edgy or Dapper to boot..
Always complaining about not finding the CD-ROM Drive and some other unexpected errors.

I really want to run linux on my desktop.. but I can't get it to boot normally.. even live won't run.

(Asus P4P800E Deluxe - 3.0Ghz HT - 2Gb DDR MEM)

---

### Post by joanartur on 2006-09-26
Hey guys ! Thank you very much for your information and help.

Today I have downloaded  the "**Edgy Eft Knot 3**" version and try it to install it.

For my surprise, although it didn't mount my "NTFS" "sata" disk partition on the "Ubuntu Live" desktop, it has been able to make partitions and start installing it in my "sata" drive.

Sadly at the 82% of the installation, while it was **configuring apt**, the installation froze.

My computer is a "**TOSHIBA Satellite Pro M70**" laptop. It has a "serial ata" drive that the "GParted" detects as a ATA HTS541060G9SA00. Its size is 55.89 GB and its path is /dev/sda.

Any idea ? ;-)

***Thank you very much !***

---

### Post by petri on 2006-09-26
You do know Edgy is still a beta? Try with Dapper CD ;) and use it till october 26th. Otherwise here's what you do:

After Dapper installation you can make a dist-upgrade like this:
In terminal: [B]SEE THE EDIT BELOW
[/B]
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
```

Change every **dapper** to **edgy**, save and close. Then back to terminal

```
sudo aptitude update
sudo aptitude dist-upgrade
```

If everything goes right after reboot you have Edgy. But be prepared it won't work as it should.


EDIT: There is a easier way to change dapper to edgy at the sources.list ([https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) ):
```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

and then
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by joanartur on 2006-09-26
Yeah Petri, I know that "Edgy" is a beta version, but the little "Dapper" can not do anything with my "Winblows designed" Toshiba and its "Serial-Ata" drive. :-D

Thank you for explaining me how to use "apt" with the terminal, but _my problem is that the installation process doesn't finish_ due to a problem with my Ethernet device (I suppose).

But thanks a lot all you guys for your interest and information !

---

### Post by rbmorse on 2006-09-26
> **Kabal said:**
> Well I've got SATA drives and PATA drives and I never got Edgy or Dapper to boot..
Always complaining about not finding the CD-ROM Drive and some other unexpected errors.

I really want to run Linux on my desktop.. but I can't get it to boot normally.. even live won't run.

(Asus P4P800E Deluxe - 3.0Ghz HT - 2Gb DDR MEM)

I've installed and run Dapper on that same configuration with no problems. It won't load/install/boot if you have a drive attached via a USB port (they're fine after install, though). For compatibility insurance I normally disconnect all USB devices except the mouse and keyboard during installs. 

Although I have an SATA optical drive, I use a PATA optical connected to the ICH5 chipset connector for booting and installs. This is more compatibility insurance.

Note that motherboard has 2 PATA (IDE) and 2 SATA ports attached to the Intel ICH5 southbridge and one IDE and 2 SATA ports connected to an outboard Sil 3112 IDE/RAID controller. K/Ubuntu won't install from a drive attached to a port controlled by the SiL chip because the installer doesn't have drivers for it (although the final install does...I think, I've never used it). 

So, make sure your box is configured with at least one PATA optical drive attached to the ICH5 IDE controller, and install from there. 

The P4P800E is a wonderful Linux platform. The only other wrinkle is that I could never get the embedded AC97 audio to work, but a $29 sound blaster PCI card fixed that. 

Within the last week I transferred my Kubuntu installation to an Intel D975XBX (aka BadAxe) with a Core2Duo E6600. The only configuration change I had to make to accommodate the swap was to reinstall ALSA-BASE to pick up support for the embedded Intel audio on the new motherboard, which now works flawlessly.

---

### Post by AndyWise on 2006-09-28
Hi 
> Sadly at the 82% of the installation, while it was configuring apt, the installation froze.

[I]Let me just say i get this from time to time when i install (same spot). And i just didn't know why does it happen. Till one day when i (and i knew about it) was having internet problems (no connection). And yes it was during the installation and it just froze. I disabled the my network card for no reason and installation continued. 

So my guess is when configuring APT install wants to check the net (to do something) but if you are not connected it just waits.[/I]

_That helped me but i don't know if you are connected to the internet during the installation or not, but if thats the case try disabling the network card._

That is done under System > Administration > Networking

> For my surprise, although it didn't mount my "NTFS" "sata" disk partition on the "Ubuntu Live" desktop, it has been able to make partitions and start installing it in my "sata" drive.

I think LiveCD never mounts existing partitions and you have to do it yourself.

---

