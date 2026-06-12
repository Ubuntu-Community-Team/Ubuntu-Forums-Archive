---
title: "[SOLVED] newbie COMPIZ+Bluetooth+MP3"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by abicash on 2007-12-18
Hi
Just yday was I able to dual boot with winxp.I dont have internet here ,I mean it can be enabled thru'
my nokia phones gprs->bluetooth->dongle which was quite simple with windows.
So i cannot apt-get anything unless bluetooth is setup.
I tried installing the gnome-vfs-obexftp.deb package but it said something about " libobex1.0 not satisfiable" (dont remember exactly since i m typing this thru' winxp).So what can be done on this?

Next I tried enabling eyecandy with compiz but even though i downloaded and ran the nvidia-glx-legacy.deb package,whenever i try enabling the thing,it says "it was not able to perform"

here is my system spec

BIOS Date: 10/24/02
BIOS Type: Phoenix-Award BIOS v6.00PG
BIOS ID:   10/24/2002-P4X266E-8235-6A6LXV5AC
OEM Sign-On: Model: P4PB 266E   BIOS revision: 1.05
Chipset:   VIA 82C3168 rev 3
Superio:   ITE 8705/SiS 950 rev 2 found at port 2Eh
CPU:       Intel Pentium(R) 4 1700 Mhz MAX: 3000 Mhz
BIOS ROM In Socket: Yes
BIOS ROM Size:      256K
Memory Installed:   768 MB
Memory Maximum:     768 MB
Memory Slot 01:     0 MB
Memory Slot 02:     512 MB
Memory Slot 03:     256 MB
ACPI Revision:      1.0

---

### Post by quinnten83 on 2007-12-18
Hi,
I can't help youwith the bluetooth, since I don't use it myself.
But could you try the command

```
lspci
```

so we can see what graphics card you have? look for where it says what graphicscard you have. The problem could be that your card is not supported.

---

### Post by abicash on 2007-12-18
I think I have NVIDIA RIVA TNT2/TNT2 Pro (as I see in winxp Device Manager)
I'll check it in Gutsy :)

And thanks for such a quick response...much appreciated..thanks


00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

---

### Post by abicash on 2007-12-18
Hi 
I am running into all sorts of troubles with Bluetooth setup
Whenever i try to connect my phone to the bluetooth dongle i read an error relating that obex is not there and a spelling mistake.So i read in forums about gnome-vfs-obexftp and I downloaded this .deb file (gnome-vfs-obexftp_0.4-1_i386.deb) .But whenever I try running it,I get an error
Error: Dependency is not satisfiable:libopenobex1
So I d/l libopenobex1-dev_1.3-3ubuntu1_i386.deb
And the error continues on this one too...
So now I am stuck in the chicken and egg problem..since my only interface to internet is thro' my cellphones gprs which can connect only thro' bluetooth!and I cannot install bluetooth support unless I have internet (it seems):confused:
I have to switch back to windows everytime I want to post something or d/l somethin on internet.
Can someone really help?Please!

---

### Post by abicash on 2007-12-18
:guitar: So I am typing this thro' my Ubuntu gutsy firefox environment.
I could do that without the gnome-vfs-obexftp d/l
what I did was, connect the phone to bluetooth dongle on rfcomm0.
Then follow this guide [www.ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_mobile_phone.2FGPRS.2FEDGE_as_Internet_modem](www.ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_mobile_phone.2FGPRS.2FEDGE_as_Internet_modem)

So the speeds r low but yes I can connect to the internet from Linux with my fone:twisted::lol::biggrin:

Now only if someone could help on Compiz..it would be great!

---

### Post by abicash on 2007-12-18
Ok now whenever I try to install a package thro' terminal I get....

abhi@abhi-desktop:~$ dpkg -i /home/abhi/Desktop/envy_0.9.9-0ubuntu2_all.deb
dpkg: requested operation requires superuser privilege


And whenever I try installing a .deb directly(doubleclicking) it says "Dependency is not satisfiable" (in this case xserver-xorg-dev)
What does this mean?

---

### Post by kpkeerthi on 2007-12-18
You have a legacy card. Do installing envy is not going to help. I suggest you install from synaptic.

```

sudo aptitude install nvidia-glx-legacy

```

And then edit  /etc/X11/xorg.conf to change "nv" to "nvidia" and reboot.

---

### Post by kpkeerthi on 2007-12-18
See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by abicash on 2007-12-18
Hi kpkeerthi :)

I have already installed a nvidia-glx-legacy.deb file and have enabled restricted drivers.But 
I am not able to turn desktop effects on.Is it that this could not be done at all on my machine?

---

### Post by zero-9376 on 2007-12-18
i am not certain but i believe aiglx/compiz support has been turned off for cards using the legacy driver

---

### Post by abicash on 2007-12-18
Oh that would be bad!It seems then I would have to get a new mother board :(

Newayz thats not important for now.
I was trying to get MP3 up and running through gstreamer and gstreamer said that there was another instance of gstreamer_good (and many more) which had to be removed in order to install gstreamer_ugly which it seems is the best one(:confused:)
So I went in Synaptic manager and removed a gstreamer_good and with it all of my audio/video/sound players.:( and still the gstreamer plugin says theres still some conflict left.
Whats all this?how can I get MP3 running?

---

### Post by perlluver on 2007-12-18
sudo apt-get install ubuntu-resricted-extras I believe, or look for it in synaptic.

---

### Post by abicash on 2007-12-19
Ok Some juggling and I am up :)
I can now play MP3/Video files with Totem.
I am loving it all...just that I am having a pretty slow internet connection!

So I can say I have reached a level where atleast I can understand what the problem is :)

---

