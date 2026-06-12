---
title: "Ubuntu constantly crashing"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-04-02
Hi again,

It has been awhile since I have last posted anything and well I am having real issues.

I installed an new Motherboard and Video Card in my PC and re-install Ubuntu and XP (I run a dual boot with grub).  Anyways, I have tried re-installing both dapper which I used before and I also tried Edgy (which flat out refused to install with my old hardware).  I am running into the same problem with both Dapper and Edgy.  After I install the first batch of updates and restart the PC everything seems fine until I shut the PC down or restart again.  At the point Ubuntu will load to the welcome screen.  I entered in my username and password. Then it attempts to load my desktop at which point my screen goes blank and kicks me right back to the login manager.  I have not been able to load my desktop successfully since.  I tried both Dapper Drake and Edgy and get exactly the same result.

Does anyone have any clue what might be doing this?  I love Ubuntu and really prefer using it.  I have XP installed to run my games, but at this point it is the only OS on my PC that will load.

](*,)

---

### Post by Patrick K on 2007-04-02
What video card do you have?

---

### Post by DanFromWinterpeg on 2007-04-02
Hi Patrick,

I have an EVGA 7600GS 256 MB DDR2 installed.  

Here is the restore of my New hardware info.


Mobo: DFI LAN Party UT DR expert
Ram: 1 GB OCZ
video: EVGA 7600Gs
HDD:two maxtor 100 GB  HDDs.  One is IDE the other is SATA.
Ubuntu is on the SATA drive. XP is on the other(in my experience, Windows and any other OS on the same drive is trouble).

---

### Post by NJC on 2007-04-02
Have you run Memtest? Wonder if a bad DIMM is causing problems..

---

### Post by DanFromWinterpeg on 2007-04-02
Ran memtest.

RAM is fine.  I tried. running Gnome failsafe safe and it crashed aswell with an error message about a problem with Gnome daemon? I think that is right.  Anyway.  It seems like it is just the GUI that is crashing.  My PC is not actually rebooting at any point. Gnome just seems to be suddenly unable to load my desktop.

---

### Post by Patrick K on 2007-04-03
I'm thinking the video card isn't setup properly. That's a common cause of the GUI not starting. I'm guess that that is an Nvidia based card.

At the command line type> sudo nano /etc/X11/xorg.confLook for a section like his:```
Section "Device"
    Identifier     "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
EndSection
```
(your's will be slightly different)
Change "nvidia" to "nv" save and reboot. If that works to start "X" then you need to reinstall the video drivers. I suggest using the Envy script (do a search for it as I don't have the link). It will get the latest drivers from Nvidia's site and install them for you.

I have no idea if this will solve your problem but it shouldn't hurt anything.

---

