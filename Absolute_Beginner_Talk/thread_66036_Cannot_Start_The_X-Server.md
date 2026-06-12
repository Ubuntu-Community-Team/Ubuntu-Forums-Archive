---
title: "Cannot Start The X-Server"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Man In Black on 2005-09-15
So, I   ordered some Ubuntu CD's a while back and recently got them. They are Hoary Hedgehog.

Anyhow, I installed to a blank hard drive, and when I boot up I get this error:

> "I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"


So I did what I found on this forum using the search:
typed in at the login:

> $ sudo dpkg-reconfigure xserver-xorg

And reconfigured everything. 


I get the same error upon booting. When I look at the output, there is one line way down that says something like "Cannot Find Screen" but the rest is greek to me.

Help! :???:

---

### Post by mlomker on 2005-09-15
You can type **nano /var/log/Xorg.0.log** to view the contents of the error messages in more detail.  It's probably an error in the /etc/X11/xorg.conf file but the reconfigure command should have recreated the file and cleared that up.

---

### Post by Man In Black on 2005-09-15
[QUOTE=mlomker]You can type **nano /var/log/Xorg.0.log** to view the contents of the error messages in more detail.  It's probably an error in the /etc/X11/xorg.conf file but the reconfigure command should have recreated the file and cleared that up.[/QUOTE]

Well, Its all greek to me.

Near the beginning it says:

> Using config file: "/etc/X11/xorg.conf"

Then way down at the very bottom, after a bunch of blah blah about settings and such it says:

> (II)ATI: Candidate "Device" section "ATI Technologies, Inc, Rage 3D II+ 215GT$ 215GTB (Mach64 GTB)

(II)ATI: Shared non-ATI VGA in PCI/AGP slot 0:19:0 detected.
(WW)ATI: PCI/AGP Mach64 in slot 0:10:0 could not be detected.
(EE)No devices detected.

Fatal sever error:
no screens found


BTW, FWIW, the onboard graphics is a ATI 3D Rage II+, but im using a NVIDIA (i think) based PCI graphics card because the onboard sucks.

Anyhow, I tried switching over to the onboard, but I dont get any display plugging into it.

---

### Post by mlomker on 2005-09-16
The answer is in the /etc/X11/xorg.conf file somewhere.  If you could attach that and the log file to a post then we could take a look.

---

### Post by Bernhard6 on 2005-09-16
[QUOTE=mlomker]The answer is in the /etc/X11/xorg.conf file somewhere.  If you could attach that and the log file to a post then we could take a look.[/QUOTE]
 I've got the same problem, with screens not found!! I don't know how to configure the PCI Settings. It writes "PCI:0:0:0" and I don't know what to write! Help!!!

---

### Post by tseliot on 2005-09-16
[QUOTE=Man In Black]Well, Its all greek to me.

Near the beginning it says:



Then way down at the very bottom, after a bunch of blah blah about settings and such it says:




BTW, FWIW, the onboard graphics is a ATI 3D Rage II+, but im using a NVIDIA (i think) based PCI graphics card because the onboard sucks.

Anyhow, I tried switching over to the onboard, but I dont get any display plugging into it.[/QUOTE]
1) get to your bios and select the graphic card you want to use (which is not the on-board one)

2) then boot Ubuntu and use the command you know to reconfigure xorg. Tell it to autodetect the card (it will be the nvidia one). Then select the driver which is "nv". And so on.

3) If it doesn't work yet use the command again and select "vesa"driver instead of "nv"

[COLOR=Red]REMEMBER to do "startx" or to reboot if you want to see the graphic interface.[/COLOR]

---

### Post by Man In Black on 2005-09-16
[QUOTE=tseliot]1) get to your bios and select the graphic card you want to use (which is not the on-board one)

2) then boot Ubuntu and use the command you know to reconfigure xorg. Tell it to autodetect the card (it will be the nvidia one). Then select the driver which is "nv". And so on.

3) If it doesn't work yet use the command again and select "vesa"driver instead of "nv"

[COLOR=Red]REMEMBER to do "startx" or to reboot if you want to see the graphic interface.[/COLOR][/QUOTE]
My computer is old, windows 98, etc, and it doesnt have anything like that in the bios. I think i have to do something with the jumpers on the mb, but i dont know how to do that.

---

### Post by tseliot on 2005-09-16
1) Ok, which driver did you use when you reconfigured xorg? "nv" or "vesa"?
2) what's your graphic card model?

---

### Post by Man In Black on 2005-09-16
[QUOTE=tseliot]1) Ok, which driver did you use when you reconfigured xorg? "nv" or "vesa"?
2) what's your graphic card model?[/QUOTE]
 I checked, and the motherboard automatically disables the onboard when a plug in card is installed.

Anyway, when I ran the config, it ddint detect the plug in card im using, just the ATI onboard. The card im using is a NVIDIA TNT2 Vanta 16M PCI VGA, S/N CGH293223.

Im going to try taking out the card, and just using the onbaord until i can get it eworking.

---

### Post by mlomker on 2005-09-16
The **lspci** command will list the devices in your machine and what ports they are on.

---

