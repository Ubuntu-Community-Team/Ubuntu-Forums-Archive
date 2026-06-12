---
title: "Please help!  Installation problems"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by aircooled76@yahoo.com.au on 2007-04-08
Hi Guys,
Have spent the last two days (and nights :) Trying to install Ubuntu on my power mac

I have finally been able to boot yaboot... but unable to install the kernel.

This is the screen I get to but can't get any further...  

[I]pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3,/install/boot.msg: Unknown or corrupt filesystem
Welcome to yaboot version 1.3.13
enter "help" to get some basic usage information

WARNING:  Bootstrap partition type is wrong: "Apple_HFS"
type should be: "Apple_Bootstrap"

Boot:  install
please wait, loading kernel...
install:3,/vmlinux: Unable to open file, Invalid device
boot:  install video=ofonly
please wait, loading kernel...
install:3,/vmlinux: Unable to open file, Invalid device
boot:  _[/I]

System Specs:  Dual 800 MHz Power PC G4  
3 hard drives and an external firewire drive... I am currently running OSX

If anyone can help me with this it would be much appreciated!!!!

thanks

Mike P

---

### Post by Sef on 2007-04-08
1) What are your computer specs?

2) Did you md5sum the download?

3) Did you burn the iso at 4x or less?

---

### Post by aircooled76@yahoo.com.au on 2007-04-08
**1) What are your computer specs?**

I have a Dual 800MHz G4 Power PC,  running OSX 10.4.6

**2) Did you md5sum the download?**

I have checked the MD5sum and the download is correct

**3) Did you burn the iso at 4x or less?**

I have reburnt the cd at 2x.... 

I tried booting computer from CD by holding the option button when it starts up... I can select the Ubuntu CD and press the arrow button... screen goes black then back to OSX option and CD option but I can't select CD (image goes fuzzy) :confused: 

Any other suggestions?

Mike

---

### Post by aircooled76@yahoo.com.au on 2007-04-09
OK I went through every file on the md5 checklist included in the download

I came accross a line where the result was "invalid argument.. (see below for script from the OSX Terminal)

md5: /volumes/ubuntu_powerpc_edgy/pool/main/i/isdnutils/isdnutils-base_3.9.20060704-1_powerpc.deb: Invalid argument

Does this mean the download is corrupt... or that there is a problem with the checksum??

Cheers

Mike

PS Very keen to get Ubuntu up and running... had a recording session today bite the dust due to OSX/ Audour techincal problems :(

---

### Post by DaDave on 2007-04-09
Dual processor? There seems to be some issues with the dual processor Macs. Could be the problem.
[http://ubuntuforums.org/showthread.php?t=185565]("http://ubuntuforums.org/showthread.php?t=185565")

---

### Post by aircooled76@yahoo.com.au on 2007-04-10
Yeah, I saw that thread.... but I can't seem to get Ubuntu to install to have the problem!!!

Im really hoping to get this up and running... what a fantastic idea Ubuntu for everyone!!!!

Mike

---

