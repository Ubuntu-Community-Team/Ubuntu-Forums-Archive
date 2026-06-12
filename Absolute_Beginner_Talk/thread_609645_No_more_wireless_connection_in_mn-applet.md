---
title: "No more wireless connection in mn-applet"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Caezar on 2007-11-11
The Wireless Connection icon is missing from the nm-applet window. I still see the "Wired Connection" and "Modem Connection", but the "Wireless Connection" disappeared.

I followed some instructions found on the web and  tried  the following remedies:
sudo killall nm-applet
nm-applet --sm-disable

sudo apt-get remove network-manager-gnome
sudo apt-get install network-manager-gnome

I also cleaned the /etc/network/interfaces text file.

But it did not give me back the icon.

What should I do?

---

### Post by kevinatkins on 2007-11-11
Hi,

You don't say what wireless card / chipset you're using but before going any further, can you check that in Administration -> Network, 'roaming mode' is enabled for the wireless connection. This is needed to allow Network Manager to manage the wireless connection.

If that doesn't work, post back And I'm assuming from your post that wireless was working for you before..

---

### Post by Caezar on 2007-11-11
Hi Kevin, thanks for your reply.

 I am running 7.10 on a Thinkpad X60. therefore, I assume my chipset is the Intel 3945ABG.

Yes, my wireless was working before. Then I probably turned off my wireless connection to save power some days ago and now the Wireless Icon in nm-applet is gone. I do not know how to get it back.

I checked inside nm-applet and the roaming mode is enabled.

Caezar

---

### Post by kevinatkins on 2007-11-11
Hi,

OK, it's possible the wireless is switched off so I'd check that. Also, if you still have no luck, could you enter in a terminal -

sudo lshw -C network

and post back the results

Cheers.

---

### Post by Caezar on 2007-11-11
I tried to follow the instructions from Ubuntu Help files to troubleshoot my wireless connection, but I did not find anything

Here is the result of the command you asked me to run:

lienol@lienol-thinkpad:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:b6:08:58
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.11.5 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
lienol@l=lienol-thinkpad:~$

---

### Post by kevinatkins on 2007-11-11
Hi,

OK, well it looks like the wireless card is being seen.. Could you check whether the driver is loaded -

lsmod | grep ipw3945

(The pipe | character is next to the 'Z' key, above the backslash on UK keyboards)

If ipw3945 isn't listed, then the driver isn't loaded so try loading it -

sudo modprobe ipw3945

I doubt there will be a problem here though - you should find the driver already loaded during boot, but anyway, worth checking...

Otherwise, bit puzzling...

---

### Post by Caezar on 2007-11-11
The driver was listed.

Maybe did I mess up with the /etc/network/interfaces file? I only have these two lines:

auto lo
iface lo inet loopback

There used to be more lines, but I deleted them, following an advice found on another forum.

---

### Post by Caezar on 2007-11-18
Well, I reinstalled Ubuntu and that did not solve my problem. I still miss the Wireless Network Interface (see attached screenshot). This is probably because I messed up the /etc/network/interfaces file.

Could anyone tell me the original content of this file?

Thanks!

---

### Post by Arthur Archnix on 2007-11-21
Have you added nm-applet to your sessions?
>system >preferences >sessions >add
The command is nm-applet --sm-disable
Description is Network Manager Applet
Ok.
Restart.

---

### Post by monte48lowes on 2007-11-21
Does your laptop have a button to turn the wireless radio on/off? My eMachines laptop works that way. If the radio is off, no wireless connections are shown.

Mike

---

