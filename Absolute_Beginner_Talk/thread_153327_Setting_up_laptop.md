---
title: "Setting up laptop"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Llwyd on 2006-03-31
Hi,

I have decided it was time to have a go with linux.  I have had a run in or two in  work with the OS and did not have a clue where to go.

I have [fingures crossed] had a successful basic installation on my laptop.  I would like to know if it is possible to set it up for wireless access.

I have searched though the forums for pcmcia threads nothing seemed to help me.  I have got an old wireless card I use to use on my laptop when I was using windows.

The biggest issue is that this wireless card is a BT Voyager (BT Voyager 1060) card and dought if it is support under linux.

Any idears

Update - Found a thread which mentioned a few things which I dont understand but looks like it gives more info about the card/slot etc wich might be useful.

pcic_probe - PCI bride probe: Texas Instruments PCI1410 found, 2 sockets.
lsmod - pcmcia_core 44932 3 pcmcia, yenta_socket, rsrc_nonstatic

Await your replies.

---

### Post by trent dillman on 2006-03-31
Well, first let's see if your card gets picked up.

Plug it in the slot & reboot, for good measure. Then, open a terminal (Applications > Accessories > Terminal) and type:

```
lspci
```

Post whatever output you get here.

---

### Post by Llwyd on 2006-03-31
trent dillman,

Thanks for getting back to me,

First thing could you explain the command to me and here is the output.

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by trent dillman on 2006-03-31
Ah, a Broadcom card...

first, lspci gives a list of the pci devices on your computer....

To get this working, install ndiswrapper-utils and ndisgtk through synaptic/adept, or use the terminal:

```
sudo apt-get install ndiswrapper-utils ndisgtk
```

Next, fire up ndisgtk as root

```
sudo ndisgtk
```

Now, you need the driver cd or the files for Windows. Install using the *.inf file. Yours is probably named bcmwl5.inf.

If you need the drivers, try downloading them from the net.

---

### Post by Llwyd on 2006-04-01
Trent,
[QUOTE=trent dillman]Ah, a Broadcom card...[/QUOTE]
Does not sound good lol
[QUOTE=trent dillman]
first, lspci gives a list of the pci devices on your computer....

To get this working, install ndiswrapper-utils and ndisgtk through synaptic/adept, or use the terminal:

```
sudo apt-get install ndiswrapper-utils ndisgtk
```

Next, fire up ndisgtk as root

```
sudo ndisgtk
```

Now, you need the driver cd or the files for Windows. Install using the *.inf file. Yours is probably named bcmwl5.inf.

If you need the drivers, try downloading them from the net.[/QUOTE]

The sudo ndisgtk when run in terminal comes back with command not found.

Thanks

P.S I looked up these commands in man but could not find ndiswrapper-utils or ndisgtk.  I only have an exe for the card driver from BT.

---

### Post by slacker990 on 2006-04-01
so what do we do after the 'sudo ndisgtk' step

I have the drivers and have loaded them. Mine are a bit different as I have a different pcmcia card (safecom SWLCT-54125) but my problem is the same.

---

### Post by pulco ant on 2006-04-01
Hey there! I also have a Broadcom card, and it *is* a bugaboo. I had to go thru the same kind of fingernail-on-a-chalkboard routine when I set up Yoper linux, Mandriva, and Fedora Core. There is a *great* step-by-step howto for you and I right here: [http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+5.10+broadcom](http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+5.10+broadcom)

It's very thorough and easy to follow, especially for a n00b like me!

Dan

---

### Post by x5452 on 2006-04-01
If you dont mind all I could really use some help in this area, I am trying to figure out how to get wireless going on my other laptop that I am running the unbuntu live cd on.  I did the lspci code in the terminal and it says host bridge: Intel Corp,  The pci wireless card is lynksys, any advice you can give me?  Do you need me to type all the code information from the terminal into here?  I would copy it but its on my other comp....

---

### Post by Llwyd on 2006-04-02
Hi,

Glad to see I am not alone lol

Do any of you have the drivers as I have only found the .sys file on the net.

Editied:
Not to worry found drivers going though process following above link.

---

