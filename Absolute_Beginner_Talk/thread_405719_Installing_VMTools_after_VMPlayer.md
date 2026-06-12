---
title: "Installing VMTools after VMPlayer"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2007-04-10
Hi, 

I've been running VMServer on one of my computer with XP as a virutal machine which works very nicely with VMTools installed. My other edgy box is a little slower so I thought I'd give VMPlayer a go as I had read it was faster than VMServer. However the mouse function on the XP virtual machine is a little sketchy and I wondered if there was any way to install VMTools on an already installed virutal machine running in VMPlayer?

Cheers.

---

### Post by caffienefree on 2007-04-10
This question might be better answered in the VMTN forums.

[http://www.vmware.com/community/index.jspa](http://www.vmware.com/community/index.jspa)

---

### Post by JoxBG on 2007-04-11
This is fairly easy. If you don't have it yet, you need to obtain the vmware tools for windows. If you already have it then what you do is mount the windows.iso image found in the lib/isoimages/ directory. The way to do this is to edit the .vmx file of your XP virtual machine (you have to shutdown the virtual machine first). If you don't have a second virtual CD-ROM, add one like:

# Settings for the optional virtual CDROM, ISO-image
#ide1:1.present = "TRUE"
#ide1:1.fileName = "/path/to/windows.iso"
#ide1:1.deviceType = "cdrom-image"
#ide1:1.mode = "persistent"
#ide1:1.startConnected = "TRUE"

where /path/to is where your windows.iso (vmware tools for windows really) image


When you reboot your XP virtual machine and login, it will detect the second CD-drive and run the installer. Just follow the prompts.

Note: If you don't have vmware tools yet, get one from vmware.com. You can download the workstation trial version and unpack the file. This will create a directory vmware/distrib where inside you can find lib/isoimages/ directory which contains all the vmware tools for different OS. You can copy the windows.iso image to your XP virtual machine directory or just point the path as described above to your download area. The important thing is to put the correct windows.iso path in your CD-ROM filename definition.

The next time you shutdown your XP virtual machine, remove the lines that you added ( or restore the original vmx file if you made a copy before the edit above) on your vmx file.

HTH
Jox

---

### Post by rikoshay on 2007-04-11
Thanks - works just fine!

---

