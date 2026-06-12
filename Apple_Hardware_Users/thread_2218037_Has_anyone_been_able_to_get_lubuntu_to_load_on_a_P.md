---
title: "Has anyone been able to get lubuntu to load on a PowerBook G4?"
date: 2014-04-19
forum: Apple Hardware Users
---

### Post by PapaNerd on 2014-04-19
Using a stock PowerBook G4 Titanium with 512MB RAM.  This was a dual boot system with MacOS plus ubuntu 10.04.  The first step was to wipe the drive (using dwipe) and create larger Linux partitions (with no MacOS partitions).  This was successful.

First installation attempt [with lubuntu-14.04-desktop-powerpc.iso]:  The live DVD booted okay and was the platform for doing the revised partitioning (above).  The first screen of the installer gave only a ghost outline of the panel with no visible content.  Got a message box when trying to close the installer, but that panel was also displayed as a ghost outline.  My conclusion was that there is not enough RAM to support both the GUI plus a graphical installation.

Second installation attempt [with lubuntu-14.04-alternate-powerpc.iso]:  The installation appeared to go normally.  However, after booting into the new lubuntu OS, a black screen is displayed.  The (white arrow) cursor is displayed against the black screen and can be moved around.  Clicking on the bottom bar where the menu should be does nothing.

Any ideas?

---

### Post by este.el.paz on 2014-04-19
> **PapaNerd said:**
>   My conclusion was that there is not enough RAM to support both the GUI plus a graphical installation.

Second installation attempt [with lubuntu-14.04-alternate-powerpc.iso]:  The installation appeared to go normally.  However, after booting into the new lubuntu OS, a black screen is displayed.  The (white arrow) cursor is displayed against the black screen and can be moved around.  Clicking on the bottom bar where the menu should be does nothing.

Any ideas?

@PN:

I did read recently that the Lubun team said they had it running on something PPC with 6xx MB RAM, so you might be under the weight on the 14.04 version, and perhaps 12.04 might work?

However, getting to the cursor against the black screen is better than nothing . . . might be you need to change the video driver to match what you have . . . or since you have installed you might need to set up an appropriate xorg.conf file . . . both are explained in various recent threads . . . possibly in the "Testers wanted for 14.04" or in the "How to get a GUI going . . ." something, something by "abtabt" linked here:

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

e.e.p.

---

### Post by Lars Noodén on 2014-04-19
Which graphics card do you have?

---

### Post by PapaNerd on 2014-04-19
Lars:  lshw output:
> product: RV250/M9 GL [Mobility FireGL 9000/Radeon 9000]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
capabilities: agp agp-2.0 pm vga_controller bus_master cop_list rom
configuration: driver=radeonfb latency=255 mingnt=8

---

### Post by PapaNerd on 2014-04-20
I pulled the disk drive from the PB G4 and attached it to the machine where I stored the G4 backups before the disk wipe.  I found this _very_ generic xorg.conf file in place under the old ubuntu 10.04 installation on the G4:
```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
After copying it to the /etc/X11 directory, I re-installed the drive and booted the PB G4.  No change in the symptoms (black screen, white moveable cursor).  One would think that if video works using the lubuntu Live CD, then the full installation should also work.

Anyone want to chime in with a known working PowerBook G4 Titanium xorg.conf file?

---

### Post by Lars Noodén on 2014-04-21
I seem to have a similar card: Radeon RV250 [Mobility FireGL 9000]

With the Alternate install I have to manually add options to the kernel to get the display to work.  When you get to yaboot try adding 'video=radeonfb:1024x768-32' or substitute in the correct dimensions of your screen:

```

Welcome to yaboot version 1.3.16
Enter "help" to get some basic usage information
boot: *Linux video=radeonfb:1280x854-32@60*

```

If that works, then it can permanently be added in /etc/yaboot.conf:

```

  label=Linux
  read-only
  initrd=/boot/initrd.img
  append="quiet splash *video=radeonfb:1280x854-32@60*"

```

Then set the changes

```

sudo ybin -v

```

It's a lot of hoops to hop through, but the bug has been outstanding for a while.  Fortunately, it can be left alone after it is set.

---

### Post by PapaNerd on 2014-04-21
Thanks Lars.  I had already tried the 1280x854 resolution in the xorg.conf file without success.  Adding ```
video=radeonfb:1280x854-32@60
``` into the yaboot file solved the problem.

---

### Post by robert94 on 2014-05-02
HELP

I too am trying to get lubuntu 14.04 to work on a Powerbook G4 [that has a broken Ethernet port] and is currently running MAC OS 10.3.9 [so I cannot resize the existing 80GB disk to create a new partition without loosing what is there...]

I have managed to get it running from a live DVD but so have have had no success booting from usb [1.1] using yaboot

When booting from the live DVD [I have to use the 'live video=ofonly' option to get the display working satisfactory and prevent the hazy screen issue]
 
The problem I now have is that I don't get any Wifi adapter showing from Network Connections. I tick allow connections to wireless and ethernet networks in user settings [live session user] but that made no difference. I then tried to create the Wifi connection under Network Connections but the Powerbook then hangs

In the ubuntu powerpc faq [here]("https://wiki.ubuntu.com/PowerPCFAQ") the above change requires a reboot but of course my live DVD is not persistant ! obviosuly I need to get the Wifi working to allow me to get new packages such as firmware-b43-installer or wicd

Any ideas ?

---

### Post by este.el.paz on 2014-05-03
> **robert94 said:**
> HELP

I too am trying to get lubuntu 14.04 to work on a Powerbook G4 [that has a broken Ethernet port] and is currently running MAC OS 10.3.9 [so I cannot resize the existing 80GB disk to create a new partition without loosing what is there...]

! obviosuly I need to get the Wifi working to allow me to get new packages such as firmware-b43-installer or wicd

Any ideas ?

@robert:

This is a quote from "farinet" from the lubun user list, discussing your very issue:  > I do not understand why there aren't in the ppc installation iso inserted by default the broadcom related firmware installation files.  They are in the ressources, but if you do not have hardwired wan access nearly no chance to get there.  First thought is that w/o ethernet I think you are better off sticking with OSX . . . you might get it up to Leopard??  Other comment is that there is a point where "boot from usb" started, mid 2000's . . . might be why it isn't working for you . . . .  I used "live-powerpc video=radeonfb:1024x768-32"  as boot parameters last night to boot the 14.04 LiveDVD into a clear GUI . . . where "radeon" would apply if you have the radeon video card & 1024x768 should match your display stats . . . the 32 came from another post and did not match the resolution number that showed in OSX partition.  Which, generally in Mac you should be doing a dual-boot setup, so if you were to fix yr ethernet yes u would have to wipe the drive, reinstall OSX, and then install linux . . . then add the wifi driver.

e.e.p.

---

### Post by robert94 on 2014-05-04
> **este.el.paz said:**
> @robert:

This is a quote from "farinet" from the lubun user list, discussing your very issue:    First thought is that w/o ethernet I think you are better off sticking with OSX . . . you might get it up to Leopard??  Other comment is that there is a point where "boot from usb" started, mid 2000's . . . might be why it isn't working for you . . . .  I used "live-powerpc video=radeonfb:1024x768-32"  as boot parameters last night to boot the 14.04 LiveDVD into a clear GUI . . . where "radeon" would apply if you have the radeon video card & 1024x768 should match your display stats . . . the 32 came from another post and did not match the resolution number that showed in OSX partition.  Which, generally in Mac you should be doing a dual-boot setup, so if you were to fix yr ethernet yes u would have to wipe the drive, reinstall OSX, and then install linux . . . then add the wifi driver.

e.e.p.

Hi thank you for the reply which I only just noticed after posting on the other thread [http://ubuntuforums.org/showthread.php?t=2220867&page=2&p=13012724#post13012724](http://ubuntuforums.org/showthread.php?t=2220867&page=2&p=13012724#post13012724)

Well I could upgrade to 10.5.8 Leopard [if I had the install DVD] but I still want to get a buntu powerpc distro working [I personally use xubuntu but that doesn't have a powerpc.iso]

But yes astonishing that the lubuntu 14.04 powerpc.iso does not include what is needed to get Wifi working since I assume the target audience for that image is Apple Powerpc devices !

What commands can I issue from 14.04 terminal to ascertain whether the ethernet port is truly dead ?

Feel free to reply on the other thread since this one is solved

---

### Post by rsavage on 2014-05-04
The firmware is not included because it would infringe copyright/whatever in the United States of America and some other countries.  Given the bizare legal system in the USA I wouldn't put it on the CD either!

---

### Post by reinhard-boris on 2014-11-10
sry double post :rolleyes: 8-[ :oops:

---

### Post by reinhard-boris on 2014-11-10
You guys need to use video=ofonly and stay away from any radeonfb variant parameter. Radeon UMS was dropped and we use KMS now, additionally you may need to use radeon.agpmode=-1 also there is no need to force any resolution, keep it simple eg. "video=ofonly radeon.agpmode=-1"

You can read more about it here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/28)

[https://lists.launchpad.net/lubuntu-qa/msg04763.html](https://lists.launchpad.net/lubuntu-qa/msg04763.html)

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

