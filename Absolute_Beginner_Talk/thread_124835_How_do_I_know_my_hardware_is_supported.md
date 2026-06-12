---
title: "How do I know my hardware is supported?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by m.musashi on 2006-02-02
I tried to find information on the Ubuntu site regarding supported hardware but couldn't find anything. Does anyone know how I can find out if my mobo is supported? It's an Asus A8N-VM CSM and so far I have not been able to install Breezy. I'm wondering if I bought the wrong board. I'm using the onboard video so my problems are probably related to some aspect of the mobo - at least I can't come up with any other possibilities.:cry: 

Thanks.

---

### Post by el3ktro on 2006-02-02
Which chipset does your mobo use? The easiest way would be to download the LiveCD and just boot Ubuntu, you'll easily see which hardware works and which not. What kind of errors are you getting? It's very unlikely that you can't even install Ubuntu ...

Tom

---

### Post by m.musashi on 2006-02-02
Here are all the stats on the mobo from the Asus web site:

- Support AMD Socket 939 Athlon 64FX / Athlon 64 X2 / Athlon 64
- NVIDIA GeForce 6150 + nForce 430
- Dual-channel DDR400
- PCI Express architecture
- Integrated GeForce6 GPU
- Dual VGA Ouput DVI-D & RGB
- NVIDIA Gigabit LAN with NVIDIA ActiveArmor Firewall
- 4 x SATA II (RAID 0, RAID 1, RAID 0+1, RAID 5)
- 1394a Support
- High Definition Audio 

I posted my errors in another thread [http://ubuntuforums.org/showthread.php?t=124677](http://ubuntuforums.org/showthread.php?t=124677)

There is definately something goofy going on and that's why I thought maybe my mobo was simply not supported. I know even Windows wouldn't recognize the NIC until I installed the drivers from the Asus Cd but it did install.

I know something must be wrong but I'm not knowledgeable enough to figure it out.

Thanks for any help.

PS the live CD won't boot either.

---

### Post by mo_x on 2006-02-02
You need to get the latest 1.0.8178 drivers from the nvidia website for the graphics. You can also download the latest nforce drivers there for ethernet en sound.
Also check the following thread on the nvidia forums:
[http://www.nvnews.net/vbulletin/showthread.php?t=57791](http://www.nvnews.net/vbulletin/showthread.php?t=57791)
If you need any help installing the drivers please let me know.

---

### Post by m.musashi on 2006-02-02
Thanks for the link. I figured it had something to do with drivers but don't I have to get Ubuntu installed first before I can update drivers? If this is going to involve recompiling the kernel then I'm SOL. That is well beyond my level of expertise. I can get a server install completed but then I get all errors as posted in my other thread. If you know what I can do when I get the fatal errors and drop to a shell that would be great. From my perspective that is a failed install and I just start over trying different options.

---

### Post by mo_x on 2006-02-02
I suggedt you boot with the nolapic noapic options you mentioned in the other thread. Then edit you xorg.conf:
sudo nano /etc/X11/xorg.conf
And change the driver to vesa. That should give you a working X.
To install the nvidia and nforce drivers you need gcc-3.4, see this thread: 
[http://www.ubuntuforums.org/showthread.php?t=79896](http://www.ubuntuforums.org/showthread.php?t=79896)

---

### Post by m.musashi on 2006-02-02
Thanks for the help. I'll give it a shot. However, after the initial install and reboot, when I get all the errors and dropped to a shell, I don't seem to be able to use sudo. It says something like "bash: sudo: command not found". I'm assuming that isn't good.

Also, is nano like vi? Can I use "sudo vi /etc..." or is nano a specific command I need to use? Sorry if that's a dumb question but I'm pretty new at this.

---

### Post by m.musashi on 2006-02-02
Sorry, one more question. When I edit the xorg.conf file and change the driver to "vesa", what, exactly is the driver I'm going to change? I'm looking at this file on an Ubuntu laptop I have set up at work and I don't see anything obvious.

Thanks.

---

### Post by mo_x on 2006-02-03
You can also use vi, any text editor will do.
In your xorg.conf there is a Device section, this is mine:
```
Section "Device"
	Identifier	"nvidia0"
	Driver		"nvidia"
	Screen		0
	BusID		"PCI:5:0:0"
	Option	"RenderAccel"	"true"
#	Option	"AllowGLXWithComposite"	"true" 
EndSection
```
You should put in there the line
```
Driver		"vesa"
```
And comment (#) the current driver.

---

### Post by m.musashi on 2006-02-04
SUCCESS! Sort of...

It seems my mobo has a defective BIOS in terms of ACPI and description tables. I don't really know what that means but apparently Linux relies on this whereas Windows doesn't. Linux can be recompiled so that it doesn't rely on the BIOS but I don't have a clue how to do that. Perhaps the developers could make that an option in Dapper. Any one know how I can make that suggestion?

Anyway, I had to give up on Ubuntu because I could not get it to work. Suse 10.0 however did install. I don't have networking or sound so I have to figure out how to add the nvidia drivers but that is further than I could get with Ubuntu. Sorry Unbuntu fans. Hopefully Dapper will address these issues and I can come back in a few months.

Thanks for all the help. At least I was able to understand my problem more or less.

---

