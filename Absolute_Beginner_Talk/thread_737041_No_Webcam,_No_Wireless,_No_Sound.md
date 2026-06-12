---
title: "No Webcam, No Wireless, No Sound"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by carlolovearianne on 2008-03-27
I just bought a new laptop. An Asus A8HE. Here are the basic specs:
 
Core Duo 1.6GHz
1 GB RAM
80 GB
DVD SuperMulti Writer

I have the luck of Ubuntu 7.10 picking up the correct resolution (1280 x 800) out of the box but it seems it's the only thing it managed to get right.

Webcam doesn't work. I downloaded Cheese to test if the webcam works but I only get a message the says "device not found".

Sound works and then not. Sound disappears when I switch tracks in Rhythmbox. Or whenever I touch the volume controls. I have to restart to get the sound back. And even that doesn't work all the time as well. I have to completely shut down and then power up most of the time to get the sound back.

Wireless card don't work. I already tried the ndiswrapper workaround (my wireless chip is an Atheros AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)). It didn't work but I'm willing to give it another try.

I bought this laptop specifically FOR Ubuntu. I'm not a Windows user who's just playing around (I'm a Mac user, anyway and once all these are fixed make that *former* Mac user). I'm aware of the possible problems with wireless cards and after reading all those how-to's, I am quite mentally prepared to deal with it. But sound is buggy?  Webcam is non-existent? Frustrating to say the least.

Please help.

---

### Post by lswest on 2008-03-27
can you post the output of ```
lspci
lshw -C network
lshw -C sound
```
(each line is a seperate command, and the second and third command's "C" argument must be capitalized)

Also, run those commands in the terminal (accessed through Applications-->Accessories-->Terminal)

---

### Post by m60dude5 on 2008-03-27
Hi. I'm not sure about the sound and webcam, but I hadd a similar problem with wireless. Check in the Hardware Manager and see if your card is recognized first. This would have saved me a lot of time. If it isn't, keep posting here cause I can't help you (I'm new to this too). If it is, enable SSID broadcasting on the router. This is what made mine work.

---

### Post by carlolovearianne on 2008-03-27
Here are the results.

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


_____________________________________________________________________________________


lshw -C network:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:09:dc:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.103 latency=0 module=r8169 multicast=yes


______________________________________________________________________________________

lshw -C sound

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel






Thanks for the quick reply.

---

### Post by carlolovearianne on 2008-03-27
i must have restarted and shut down the laptop more than ten times now for the entire day just to get the sound back.

Please help me

---

### Post by Astura on 2008-03-27
My sound issues were resolved when I upgraded to Hardy Heron, maybe try that

Other wise I too am with you, no wireless and no webcam

---

### Post by which_chick on 2008-03-27
The wireless card may be identifying itself incorrectly.

Atheros 5006 is supposed to work out of the box.  Often, when there are errors with wireless and this alleged card, it's not the card it says it is.  The 5007eg misidentifies itself as a 5006, see.

Check to see if you have a mis-identifying-itself 5007:

From [http://home.nyc.rr.com/computertaijutsu/rhhw.html](http://home.nyc.rr.com/computertaijutsu/rhhw.html)

> As I said, the AR5007EG is not identified properly by lspci. One thing that will help you determine if you're one of the lucky ones with it is to do lspci -nn. This will show the ID's. If you get 168c:001c as the ID number, then there's a good chance that you have that card.

If you *do* have that card, there's a workaround that is functional on i386 architecture.  More information (links, step-by-step howto) available in the following thread:

[http://ubuntuforums.org/showthread.php?t=732945](http://ubuntuforums.org/showthread.php?t=732945)

---

### Post by carlolovearianne on 2008-03-28
Thanks for the help guys!

I'm going to try and solve the issues one at a time. First thing first is sound. I have more than 3000 mp3 and vorbis files and that I guess speaks for itself.

I can live without the webcam, though it's nice to have it working.

The wireless can wait (for now).

I'm going to upgrade to Hardy right now, wish me luck.

I love Ubuntu (the look, the package, the philosopy) but this is so inconvenient and frustrating to say the least...

---

### Post by superprash2003 on 2008-03-28
you could try fixing the sound by following this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by carlolovearianne on 2008-03-28
Just upgraded  to Hardy and thank God my sound is fixed!

And also while booting the wireless light on the laptop lit up but I checked Network and there is still no option for wireless. But then again that can wait.

Anybody have any ideas how to make Hardy remember that my resolution is 1280 x 800? I already rebooted twice (once when I tried Rhythmbox to test the sound) and from boot up it tells me that it's "running on low graphics..."

I have to reconfigure the video card from Other-Screen and Graphics and set the driver to intel experimental modesetting.

Haven't tried the webcam if it's working now.

One step at a time...

---

### Post by MONODA on 2008-03-28
i strongly suggest trying another distro and maybe coming back later. the reason for this is if you have more than 2 pieces of hardware not working, the distro will not work well.

---

### Post by lswest on 2008-03-28
well, can you post the output of ```
cat /etc/X11/xorg.conf
``` if the settings are low in there, you can change them (with help from us, or not, up to you) always remember to back it up though! ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
and to restore: sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by carlolovearianne on 2008-03-28
Got the resolution working correctly now. :)

So I got the sound working. I'm sort of happy. Hardy looks good and I can't wait for the official release.

I know there are countless of wireless how-to's so I'm going to try and fix it last.

Next stop: Webcam. With that I don't even know where to start.

Any ideas, anybody?

---

### Post by lswest on 2008-03-28
well, do you know what webcam exactly it is? or see what the output of ```
lspci
lsusb
``` is, and try to find info on if it has drivers for linux, if anyone was able to get it to run, etc.  and thanks for the thanks ^^ (i had a hell of a time finding out where it came from :P i ended up going through every single post i made in the last 2 weeks to find it XD, wish they'd implement the "find all thanked posts" feature soon :P)

---

### Post by MONODA on 2008-03-29
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
[http://www.linux.com/base/ldp/howto/Webcam-HOWTO/index.htmlt](http://www.linux.com/base/ldp/howto/Webcam-HOWTO/index.htmlt)
good job on getting stuff to work

---

### Post by carlolovearianne on 2008-03-29
lscpi results:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

I don't have an idea which one of those pertains to the laptop's webcam :).

But I think I'll wait 27 days for the Hardy to be officially released hoping that a lot of things will be fixed. I'll leave things as it is for the meantime. Right now I'm quite happy getting the sound working as it is, but of course it could be better.

---

### Post by lswest on 2008-03-29
can you also post the output of ```
lsusb
``` since my HP laptop has an integrated webcam, but it is recognized as a USB device.  Can't see any that looks like it could be a webcam in the PCI slot, which isn't surprising.  And yes, chances are Hardy will fix a lot of things :P

---

### Post by Tomatz on 2008-03-29
To me it sounds like a problem with hal.

Try updating hal through synaptic :)

---

### Post by carlolovearianne on 2008-03-29
Thanks for all the help guys!

I understand Hardy (which I'm using right now) is as fragile as an egg shell :). I'm fine with things as it is. Really, I'm glad the sound is working as it is. The rest of them webcam and wireless I'm going to wait until Hardy is officially released.

I'm enjoying things as it is and it's fast (attributable to laptop, in part, it running a dual core processor) and very pleasing to the eye. I can't wait until the final release.

Once Hardy is out and what's needed to be fixed still isn't I hope you guys can still lend a helping hand to a switcher like me.

---

### Post by lswest on 2008-03-30
Sure, I'd be happy to help ^^

---

### Post by madscience on 2008-04-08
I have the exact same laptop, and after installing the Hardy beta, I had no problem with the sound, wireless and webcam.  The only problem I'm having is that the wireless light is not lit and Fn-F2 does not toggle it or disable wireless.  I'm waiting for Hardy final to see if it gets resolved.

---

