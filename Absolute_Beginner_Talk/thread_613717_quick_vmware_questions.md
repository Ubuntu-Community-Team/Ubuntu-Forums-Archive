---
title: "quick vmware questions"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by svtfmook on 2007-11-15
i have a lexmark printer/scanner that is not compatible with linux.

the only thing i use it for is scanning.

would i be able to use my xp install through vmware to scan pictures?

would i need to install my motherboard chipset drivers?  video driver?  etc in vmware?

he only thing i have to boot to windows for is scanning photos and playing battlefield, lol.  trying to eliminate 50% of my windows work.

---

### Post by spupy on 2007-11-15
I'm sorry, but I don't think the printer would work in VMware if it doesn't work under Linux. VMware uses a kernel module, so that makes me think that the kernel must first find and connect to the hardware, and then the kernel module for vmware presents that particular device "virtualized" to the operating system in the virtual machine.

---

### Post by shad0w_walker on 2007-11-15
As far as I am aware Virtual box is capable of directly accessing USB hardware so it could work in VMware. Give it a try and find out is probably the easiest way to tell.

---

### Post by spupy on 2007-11-15
> **shad0w_walker said:**
> As far as I am aware Virtual box is capable of directly accessing USB hardware so it could work in VMware. Give it a try and find out is probably the easiest way to tell.

Yes, if it is USB, it will probably work, in VMWare, too.

---

### Post by svtfmook on 2007-11-15
what about all the chipset/video drivers?  do they need to be installed?

---

### Post by spupy on 2007-11-15
In the guest OS you should install VMWare Tools. It contains some tools and drivers for the virtual machine. (Since the hardware the guest sees is not the same as your actual hardware. IIRC, the emulated hardware is always the same for each guest OS.) In fact, in my case, i didn't need any extra drivers besides the ones shipped with windows, but after installing vmware tools, the performance and responsiveness of the guest OS increasen dramatically!

---

### Post by svtfmook on 2007-11-16
ok, i tried vmware-server, couldn't get it run run and it soaked up 50% of my memory.

i got vbox running, installed windows, but had no USB support.

---

### Post by spupy on 2007-11-16
> **svtfmook said:**
> ok, i tried vmware-server, couldn't get it run run and it soaked up 50% of my memory.

What problems did you have with vmware server?

---

### Post by paradoxni on 2007-11-16
> **svtfmook said:**
> i got vbox running, installed windows, but had no USB support.

the version in synaptic is the OSE version which lacks some features (like usb support), remove it then download the package from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) , its still free for personal use, just not open source like the OSE version, but it does support USB. IT also supports desktop integration, where you would have your gnome and XP desktop displayed together at the same time and programs in XP load up as if they were running from gnome, which i thought was impressive :)

---

