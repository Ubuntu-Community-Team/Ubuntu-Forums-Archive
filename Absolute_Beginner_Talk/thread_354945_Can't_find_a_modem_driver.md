---
title: "Can't find a modem driver"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Jensor on 2007-02-06
I can't seem to find a modem driver. Here is my set up:
intel 386 motherboard
8 GB drive
256M ram
 running scanModem I find:
CPU=i686
Ubuntu 6.06.1 LTS
Linux version 2.6.15-magma
Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem
Support type needed: hcflinmodem

When I go to [www.linuxant.com/drivers](www.linuxant.com/drivers) I find and download crxtinstall.run.
When i executed that program I got an e3rror saying that it couldn't connect to get the information it needed to complete its task. 
Duh! Why did it think it could connect before it finished installing the modem driver?
Any way it listed an alternative to go to [http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php)
to get the full download of the install file. However, there is not a listing there for my kernal version.  
They offered the alternative of downloading a generic package with source instead and point out that kernal source and the gcc C compiler must  be used to dynamically build the driver modules upon installation.

Am I going down the right path? I'm beginning to think that maybe I should just purchase an external modem and hope that I can get it to work with my setup. 
Can any one give me some guidance here?

Jack Ensor

---

### Post by sloarch07 on 2007-02-24
I just set up one of these modems and got it to work just fine.  The only down side is that linuxant charges you for the full speed version of the driver.  

When you run "uname -r" what is the output?

---

