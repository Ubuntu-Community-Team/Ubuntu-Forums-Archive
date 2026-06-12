---
title: "Need a little help.."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Chiariman on 2007-12-16
Okay, I've only been using Ubuntu for a couple of days now... and now I would like to be able to install/run games, the main one is World of Warcraft. I have gone through numerous guides I have found on the internet, and due to lack of experience with Linux, I am having a hard time. The furthest I have gotten is I have gotten the game to run, but it is horribly laggy. I don't know what I am missing, I would appreciate any help. Thanks.

---

### Post by spiderbatdad on 2007-12-16
did you see this:[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Chiariman on 2007-12-16
> **spiderbatdad said:**
> did you see this:[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I did the first step, the graphics card check and I got

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17

I have ran WoW on this comp when I had Windows, so I know it'll run.

---

### Post by spiderbatdad on 2007-12-16
what output do you get if you type ```
lspci
```in a terminal?

---

### Post by Chiariman on 2007-12-16
> **spiderbatdad said:**
> what output do you get if you type ```
lspci
```in a terminal?

Well, I typed it in and this is what I got, I 'm not entirely sure which part you want. But here's all of it. :P 

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
05:05.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

---

### Post by spiderbatdad on 2007-12-16
ok have you installed an nvidia driver for your graphics card? or do you have a driver listed in the restricted driver manager that is not checked?

---

### Post by Chiariman on 2007-12-16
> **spiderbatdad said:**
> ok have you installed an nvidia driver for your graphics card? or do you have a driver listed in the restricted driver manager that is not checked?

I have tried getting the drivers, but with no avail. I have downloaded the most current drivers to my desktop and I then tried to install them, but every time I click on the icon I get a WINE error. 

"Wine has exited with a  failure status of 193." and it goes on..

---

### Post by spiderbatdad on 2007-12-16
here's a screenshot of packages in synaptic that may be of help...you would need the dev as well as some or all of the other...maybe. Good luck, this is beyond my knowledge really, but i believe you can resolve the problem.

---

### Post by Chiariman on 2007-12-16
> **spiderbatdad said:**
> here's a screenshot of packages in synaptic that may be of help...you would need the dev as well as some or all of the other...maybe. Good luck, this is beyond my knowledge really, but i believe you can resolve the problem.

Okay, I will give it a shot. Thank you very much for the help.

---

### Post by spiderbatdad on 2007-12-16
Private Message: w00t
 
13 Minutes Ago
Chiariman Chiariman is online now
First Cup of Ubuntu
	  	
Join Date: Dec 2007
Beans: 5
w00t
Hey, what you said to do worked. Thank you very much, you have no idea how much time you just saved me, lol. Thanks again, much appreciated.
__________________
Forward Message

I assume from this PM the nvidia-glx packages solved your problem? If that's what you meant it would be nice to post here (hope you don't mind) so that others may benefit. Nice too if titles are more specific (not a criticism) it helps folks find answers through searches, without having to post on similar topics.

---

