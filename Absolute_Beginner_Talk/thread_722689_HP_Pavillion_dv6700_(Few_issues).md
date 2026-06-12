---
title: "HP Pavillion dv6700 (Few issues)"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by jokersloose on 2008-03-12
Hello,

I just installed Ubuntu 7.10 on my son's HP Pavillion dv6700 and I'm having a heck of a time with a few things. 

1. The video setting will not stay at the 1280x800, I did get Envy installed the Restricted Driver enabled. When I'm in my Nvida control settings I change it too 1280x800 tell it apply and it changes my screen to that. Then when I click "Save to X Config file" I get Unable to create new X config backup file '/etc/X11/xorg.conf.backup'. So my question is: Do I replace the entire file Nvidia shows me with the one in the /etc/X11/xorg.conf (making a back up of the org of course). Or is there something else I'm missing?

2. Wireless (duh, huh? LOL) I can't for the life of me to get this too work. 

lspci -v

 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137a
        Flags: fast devsel, IRQ 21
        Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

iwconfig

lo        no wireless extensions.

eth8      no wireless extensions.

sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth8
       version: a2
       serial: 00:00:6c:79:61:cf
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.112 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

I did look at some of the other threads but couldn't find any thing that worked. 

3. Headphones/Mic: I have sound and the touch hot keys work. WOW!! Now I need to get the headphones/mic to work.  I need the on board mic and the headphone/mic jack to both work. If that's possable. I opened alsamixer, but don't have any options for headphones and/or mic. So do I need to update my alsa file? Or what?

4. Webcam: I also need to get the web cam up and going. Have no idea where to even start looking for a fix on this one. 

5. When I minimize a window it goes away. It doesn't show up in the task bar. Now I did delete the bottom panel and moved the top panel to the bottom. That's the look my son wanted.  

I do understand some basic commands in Linux. So if there is a "how-to" on any of these just point me in the right direction. 

Thanks for any and all help. Just let me know if you need any more information posted.

Thanks,
James

---

### Post by Ecclesia on 2008-03-13
I can't help you with many of your issues, but you will get your minimized window list back by right clicking on the panel and adding "Window List" to it.

About the headphone jacks, there's a post here:[http://ubuntuforums.org/showthread.php?t=676917](http://ubuntuforums.org/showthread.php?t=676917)

For wireless and webcam, it would be helpful if you post what the specs are.  Start by posting the output of running "lspci" from /sbin.

---

