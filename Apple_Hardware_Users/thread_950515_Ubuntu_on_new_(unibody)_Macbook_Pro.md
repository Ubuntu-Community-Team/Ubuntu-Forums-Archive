---
title: "Ubuntu on new (unibody) Macbook Pro?"
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by enigma_0Z on 2008-10-17
I'm considering a mac for my next purchase, and of course I'd put Linux on it...

But, I'd *like* to get one of the latest-and-greatest MacBook pro's - The new thinner unibody MacBook Pro... I understand that the hardware is (somewhat) bleeding edge, however, so my question is could I run ubuntu on it?

I'm comfortable with hacking around in Ubuntu to get it running, as long as it's stable once I'm done.

So, can it be done/has it been done?

---

### Post by surj08 on 2008-10-17
ohhh thats right ubuntu doesnt have the powerpc edition like some of the other distros... im sure it can be done tho!

ill be able to let you know in a few weeks becuase im getting the new MBP anywho and will try to get ubuntu on it!

---

### Post by enigma_0Z on 2008-10-17
> **surj08 said:**
> ohhh thats right ubuntu doesnt have the powerpc edition like some of the other distros... im sure it can be done tho!

ill be able to let you know in a few weeks becuase im getting the new MBP anywho and will try to get ubuntu on it!

AFAIK the new MBP is intel, not ppc...

---

### Post by kosumi68 on 2008-10-17
enigma,

it will definitely work eventually, but it is difficult to know before trying, exactly what the difficulties will be. Whomever gets the new machine first would be making the community a big favor by reporting as many problems here as quickly as possible. Here are some diagnostic tools to try out:

```

sudo dmidecode | grep 'Product Name:'

```
We will need to know the exact product names of these beauties.

```

lsusb

```
An overview of the USB devices

```

sudo scan-smc.sh

```
Script to map out the SMC keys, available in this post: [http://ubuntuforums.org/showpost.php?p=5830393&postcount=11](http://ubuntuforums.org/showpost.php?p=5830393&postcount=11)

```

sudo lsusb -vv -d 05ac:<trackpad device id>

```
All details of the trackpad device, which presumably is similar to the Macbook Air, but most likely has a new device id (which can be found by the output of lsusb).

Furthermore, the nvidia chips might pose problems, but others will be better suited to deal with those questions.

---

### Post by enigma_0Z on 2008-10-17
Well, I'll probably have the money for a new one by May... so hopefully most of the kinks will be worked out by then...

AFAIK Mac OSX operates the nVidia chips by running dynamically in SLI mode for games, running the 9600 chip for higher performance apps, and the 9400 chip for typical desktop usage. I would think that the binary nVidia driver should do/handle all of this?

---

### Post by cyberdork33 on 2008-10-17
> **enigma_0Z said:**
> AFAIK Mac OSX operates the nVidia chips by running dynamically in SLI mode for games, running the 9600 chip for higher performance apps, and the 9400 chip for typical desktop usage. I would think that the binary nVidia driver should do/handle all of this?
That could be a bad assumption. First, since I think this the first time this hardware has made an appearance, there is likely not (full) support for it in the proprietary or open drivers. We have had trouble on new nvidia hardware in Macs before... then again, it could "just work" and surprise us all.

We were discussing some of this in this thread too:
[http://ubuntuforums.org/showthread.php?t=947947](http://ubuntuforums.org/showthread.php?t=947947)

---

### Post by kellusion on 2008-10-17
I'm getting mine today!!!  I'll keep you posted with whatever I figure out. I'm super pumped for my first intel mac and this is one of the big reasons. :D

---

### Post by Tlalock on 2008-10-17
I was under the impression that the new MBP setup did not include a full SLI.  I could be wrong, but I heard that the user decided on boot which GPU to use.  Parallel processing, therefore, would not be possible in a sense.  

In that case, I think only the driver for one or the other card would be necessary, but how which driver is used I have no idea, perhaps the default 9400?  But I don't know.  Can anyone verify this?

---

### Post by Spark* on 2008-10-17
One has to choose the GPU in the preferences, then log out (not reboot) to switch. It is unclear whether future versions of OSX might allow the switch without logging out, but in any case the driver is not doing anything automatically.

It was also said that running under Windows, it will always use the faster discrete card, so I assume that it would be the same under Linux by default.

---

### Post by enigma_0Z on 2008-10-17
> **Spark* said:**
> One has to choose the GPU in the preferences, then log out (not reboot) to switch. It is unclear whether future versions of OSX might allow the switch without logging out, but in any case the driver is not doing anything automatically.

It was also said that running under Windows, it will always use the faster discrete card, so I assume that it would be the same under Linux by default.

Good to know. However, I'd imagine that the two cards have different PCI ID's and would thus be switchable in Linux, after a restart of the X server (accomplishes basically what a logout/in does on the Mac)

---

### Post by cyberdork33 on 2008-10-17
> **Spark* said:**
> One has to choose the GPU in the preferences, then log out (not reboot) to switch. It is unclear whether future versions of OSX might allow the switch without logging out, but in any case the driver is not doing anything automatically.

It was also said that running under Windows, it will always use the faster discrete card, so I assume that it would be the same under Linux by default.

> **enigma_0Z said:**
> Good to know. However, I'd imagine that the two cards have different PCI ID's and would thus be switchable in Linux, after a restart of the X server (accomplishes basically what a logout/in does on the Mac)

Both very interesting points. If it is like most other things we have found, you might be able to select the card in OSX and reboot into Linux, and the same card will be active. I would guess that OSX will modify some EFI variable that determines which card will be used, but one card will be used by default from a cold boot. Unfortunately, the EFI variables are pretty much unknown territory right now...

---

### Post by enigma_0Z on 2008-10-17
> **cyberdork33 said:**
> ... I would guess that OSX will modify some EFI variable that determines which card will be used, but one card will be used by default from a cold boot. ...

Pardon my ignorance... what's EFI?

---

### Post by cyberdork33 on 2008-10-17
> **enigma_0Z said:**
> Pardon my ignorance... what's EFI?
It is what Apple uses instead of a BIOS. It is the computer's base firmware code. There are some mods to the Apple version of it though... (like the addition of an HFS+ driver), and there is no "config screen" like on a typical PC. Previously apple used "Open Firmware" on its PPC machines.

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

---

### Post by inchaos on 2008-10-17
> 
Both very interesting points. If it is like most other things we have found, you might be able to select the card in OSX and reboot into Linux, and the same card will be active. I would guess that OSX will modify some EFI variable that determines which card will be used, but one card will be used by default from a cold boot. Unfortunately, the EFI variables are pretty much unknown territory right now...

Well, we know at this point there's no Hybrid SLI support.  Right now, it's Vista only.  Hopefully by/with Snow Leopard, something will emerge to surprise and delight us all.  I have no idea if it pertains to this point, but according to nVidia, with Bootcamp, you'll use whichever graphics card was last used in OS X.  According to Apple, however, you'll only be able to use the integrated 9400 card.  This is, obviously, for XP.

> 
Pardon my ignorance... What's EFI?
EFI stands for extensible firmware interface.  It accomplishes the same task as BIOS on PC's or Open Firmware on PPC Macs.

---

### Post by cyberdork33 on 2008-10-17
> **inchaos said:**
> ...according to nVidia, with Bootcamp, you'll use whichever graphics card was last used in OS X.
This seems to go along with my theory as well.

---

### Post by Psy-Q on 2008-10-28
Here's the output from our first unibody MBP:

dmidecode:
```

	Product Name: MacBookPro5,1
	Product Name: Mac-F42D86C8
```


lsusb:

```
Bus 004 Device 005: ID 05ac:820b Apple Computer, Inc. 
Bus 004 Device 004: ID 05ac:820a Apple Computer, Inc. 
Bus 004 Device 003: ID 05ac:8213 Apple Computer, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05ac:0237 Apple Computer, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ac:8507 Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

lspci:
```

00:00.0 Host bridge: nVidia Corporation Unknown device 0a82 (rev b1)
00:00.1 RAM memory: nVidia Corporation Unknown device 0a88 (rev b1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 0aae (rev b2)
00:03.1 RAM memory: nVidia Corporation Unknown device 0aa4 (rev b1)
00:03.2 SMBus: nVidia Corporation Unknown device 0aa2 (rev b1)
00:03.3 RAM memory: nVidia Corporation Unknown device 0a89 (rev b1)
00:03.4 RAM memory: nVidia Corporation Unknown device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation Unknown device 0aa3 (rev b1)
00:04.0 USB Controller: nVidia Corporation Unknown device 0aa5 (rev b1)
00:04.1 USB Controller: nVidia Corporation Unknown device 0aa6 (rev b1)
00:06.0 USB Controller: nVidia Corporation Unknown device 0aa7 (rev b1)
00:06.1 USB Controller: nVidia Corporation Unknown device 0aa9 (rev b1)
00:08.0 Audio device: nVidia Corporation Unknown device 0ac0 (rev b1)
00:09.0 PCI bridge: nVidia Corporation Unknown device 0aab (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0ab0 (rev b1)
00:0b.0 IDE interface: nVidia Corporation Unknown device 0ab5 (rev b1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0ac4 (rev b1)
00:15.0 PCI bridge: nVidia Corporation Unknown device 0ac6 (rev b1)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0ac7 (rev b1)
00:17.0 PCI bridge: nVidia Corporation Unknown device 0ac7 (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0647 (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems Unknown device 5901 (rev 06)
```

lsusb from trackpad:
```

Bus 004 Device 005: ID 05ac:820b Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x820b 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered
```

This is running Hardy from the live CD. Screen resolution was not detected properly, but that's to be expected with all the unknown devices. I will try Intrepid as soon as it's final.

---

### Post by kosumi68 on 2008-10-28
> **Psy-Q said:**
> Here's the output from our first unibody MBP:

dmidecode:
```

	Product Name: MacBookPro5,1
[...]
Bus 003 Device 003: ID 05ac:0237 Apple Computer, Inc. 

```

This is running Hardy from the live CD. Screen resolution was not detected properly, but that's to be expected with all the unknown devices. I will try Intrepid as soon as it's final.

So you have the ISO (european) version of the keyboard. Excellent - there was until now no confirmation of this device id. Chances are very good that you will get most things working with Intrepid and the mactel patches described in this thread. :-)

---

### Post by Psy-Q on 2008-10-29
> So you have the ISO (european) version of the keyboard.

Oh -- yes, I forgot to say :)  It's a Swiss-German keyboard. You sound hopeful about getting Intrepid up and running without too much trouble, that's great.

I do wonder about the trackpad during installation, though. With the live CD, it's nearly impossible to use. Since the whole bottom of the pad is a button and tap-clicks don't seem to register, you need to remember to take your index finger off the pad to click. Dragging is also a headache, as having two fingers (one for the click, one for the drag) on the touchpad at the same time seems to confuse it.

But if that's our only worry, great. I actually don't work in our Mac OS X department, but as soon as ext3 partitions work correctly in Deploy Studio Pro, I'll set up some HD images for Ubuntu on MacBook. Then those of our students interested in Ubuntu can get a rEFIt install and a pre-configured Ubuntu image from us. This is at an art university, so don't expect miracles, by far most of the students only want OS X ;)

---

### Post by Psy-Q on 2008-10-29
Good news from the Intrepid RC front:

WLAN works out of the box on the MBP, resolution is properly detected (loads the nv driver instead of vesa). Function keys (brightness, volume) do not work.

A few less unknown devices thanks to the new pci.ids etc.:

lspci:

```
00:00.0 Host bridge: nVidia Corporation Device 0a82 (rev b1)
00:00.1 RAM memory: nVidia Corporation Device 0a88 (rev b1)
00:03.0 ISA bridge: nVidia Corporation Device 0aae (rev b2)
00:03.1 RAM memory: nVidia Corporation Device 0aa4 (rev b1)
00:03.2 SMBus: nVidia Corporation Device 0aa2 (rev b1)
00:03.3 RAM memory: nVidia Corporation Device 0a89 (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation Device 0aa3 (rev b1)
00:04.0 USB Controller: nVidia Corporation Device 0aa5 (rev b1)
00:04.1 USB Controller: nVidia Corporation Device 0aa6 (rev b1)
00:06.0 USB Controller: nVidia Corporation Device 0aa7 (rev b1)
00:06.1 USB Controller: nVidia Corporation Device 0aa9 (rev b1)
00:08.0 Audio device: nVidia Corporation Device 0ac0 (rev b1)
00:09.0 PCI bridge: nVidia Corporation Device 0aab (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation Device 0ab5 (rev b1)
00:0c.0 PCI bridge: nVidia Corporation Device 0ac4 (rev b1)
00:15.0 PCI bridge: nVidia Corporation Device 0ac6 (rev b1)
00:16.0 PCI bridge: nVidia Corporation Device 0ac7 (rev b1)
00:17.0 PCI bridge: nVidia Corporation Device 0ac7 (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)
```

lsusb:

```
Bus 004 Device 005: ID 05ac:820b Apple, Inc. 
Bus 004 Device 004: ID 05ac:820a Apple, Inc. 
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:0237 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jimmij01 on 2008-10-29
I also have one of the new Macbook Pros. I am running the latest 8.10 packages. I have also added the packages from the mactel ppa.  The only things that don't work are:

1) LCD Screen brightness
2) Sound only works with headphones

Things that are working:

1) Media Keys
2) Keyboard brightness key
3) Sensors(playing neverball)
4) Wireless

On a side note, battery life seems terrible. I'm not sure if this is directly related to the screen brightness or not. I am migrating from a Macbook 4,1 where the battery life was much better.

Please let me know what I can provide to get this thing supported.

---

### Post by cyberdork33 on 2008-10-29
> **Psy-Q said:**
> WLAN works out of the box on the MBP...

> **jimmij01 said:**
> 
Things that are working:

4) Wireless

This is interesting to note because there are a few people posting that cannot get it to work for some reason or another. Do you know what driver you are using?

---

### Post by jimmij01 on 2008-10-29
Product Name: MacBookPro5,1
	Family: MacBook Pro
	Product Name: Mac-F42D86C8
	Version: Mac-F42D86C8

04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

filename:       /lib/modules/2.6.27-7-generic/volatile/wl.ko
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        ieee80211_crypt
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
license:        MIXED/Proprietary
parm:           oneonly:int
parm:           piomode:int
parm:           nompc:int
parm:           name:string

---

### Post by jimmij01 on 2008-10-29
Something new I just came across.  When rebooting, the machine does not go all the way down and reboot.  It shutdown, but never powers off.  I have to manually hold the power button to turn the machine off and then manually power it on to reboot.

On the flip side, Suspend and Hibernate are both working perfectly for me.

---

### Post by kosumi68 on 2008-10-29
> **jimmij01 said:**
> I also have one of the new Macbook Pros. I am running the latest 8.10 packages. I have also added the packages from the mactel ppa.  The only things that don't work are:

1) LCD Screen brightness
2) Sound only works with headphones

Things that are working:

1) Media Keys
2) Keyboard brightness key
3) Sensors(playing neverball)
4) Wireless

On a side note, battery life seems terrible. I'm not sure if this is directly related to the screen brightness or not. I am migrating from a Macbook 4,1 where the battery life was much better.

Please let me know what I can provide to get this thing supported.

I presume you got the trackpad to work as well.

1) LCD brightness: unknown territory here, but the most likely culprit would be no current support in XRandR. If you cannot get xbacklight to work, it is even more likely, since it is using the same method.

2) You tested the standard solution, adding the 'options snd_hda_intel model=mbp3' in /etc/modprobe.d/alsa-base?

Battery is interesting. The program 'powertop' is excellent to check what drains your power, if you havent tried it. Running the processor on power save, reducing screen brightness, using laptop-mode, all those help. Even though a different machine, maybe this page helps: [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

---

### Post by jimmij01 on 2008-10-29
xbacklight just says "No outputs have backlight property"

jimmij@laptop:~/Desktop$ grep -i mbp3 /etc/modprobe.d/*
/etc/modprobe.d/alsa-base:options snd_hda_intel model=mbp3

I've played with powertop a bit. I'll spend some more time with it.

---

### Post by Psy-Q on 2008-10-30
jimmij01, good point, our test model also never shuts down without forcing it to do so.

About the bad battery life: Let's find out if frequency scaling (powernowd, cpufreq or one of those) works on the MBP. Is yours getting very hot when running GNU/Linux as well? I suppose frequency scaling isn't working, and I also believe that the graphics card is running full steam all the time. That would explain the bad battery life etc.

I'm quite sure the nv driver doesn't support PowerMizer or any other frequency scaling/power saving. Have you tried the proprietary Nvidia driver? That plus nvidia-settings should be able to tell you if PowerMizer works and how fast the GPU core is running.

---

### Post by Nikos.Alexandris on 2008-11-04
Hi all!

Not sure if I should follow this thread or the other one entitled "New Macbook Ubuntu Ready???" [1]

So, I am a new tester with a MBP 5.1 for 3-4 days. It depends on what finally works and what not and if there are any dangerous issues (like the one with the temperature).

I don't know from where exactly to start since I read some rEFIt and some BootCamp only solutions.

I am not interested in working with OSX. But I understand that it's good to have it for firmware updates.

Any "first things to do" hints are welcome.

Cheers, Nikos

[1] [http://ubuntuforums.org/showthread.php?t=947947](http://ubuntuforums.org/showthread.php?t=947947)

---

### Post by cyberdork33 on 2008-11-04
> **Nikos.Alexandris said:**
> I don't know from where exactly to start since I read some rEFIt and some BootCamp only solutions.

I am not interested in working with OSX. But I understand that it's good to have it for firmware updates.

Any "first things to do" hints are welcome.
I would definitely keep OS X around for update especially on such new hardware. Another option is to install it on an external hard drive which you can boot to only to get updates.

Basically, If you want to dual boot, start with rEFIt, and partition with BootCamp. then boot the ubuntu live cd and start gparted. With gparted, delete the bootcamp partition and install Ubuntu to the "largest free space".

If you plan to eliminate OSX from the drive, just boot the LiveCD and tell it to use the entire disk.

---

### Post by Nikos.Alexandris on 2008-11-04
> **cyberdork33 said:**
> I would definitely keep OS X around for update especially on such new hardware. Another option is to install it on an external hard drive which you can boot to only to get updates.

Basically, If you want to dual boot, start with rEFIt, and partition with BootCamp. then boot the ubuntu live cd and start gparted. With gparted, delete the bootcamp partition and install Ubuntu to the "largest free space".

If you plan to eliminate OSX from the drive, just boot the LiveCD and tell it to use the entire disk.


cyberdork33, thank you a lot. I finally left OSX exist :-). I don't have currently any external device with more than 10GB (that's what it needs for minimum, right?).

Initially I couldn't resize the OSX partition (using diskutil from within OSX). I erased and re-installed (in a "case-sensitive" partition). I reduced the OSX partition to 23.something GB.

Now, I bootet with Ubuntu 64-bit. It seems that the description in [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) is a bit different from your recomendation(?). Or does it not make any big difference (that is: partition-ing with BootCamp everything  or  just have free space and partition-ing with gparted). I already followed the steps described in previous link -- so I have to go through this.

I will go ahead and try the XFS filesystem. Is it a bad idea?

Kind regards, Nikos

---

### Post by Nikos.Alexandris on 2008-11-04
So, if I get it right there is now way to have more than 4 partitions?

One is the OSX and another one the EFI. I would like to split Linux in "/", "/home" and "swap", that is another 3 partitions. Or should I just forget the idea... ?

Any help highly appreciated, Nikos

---

### Post by cyberdork33 on 2008-11-04
> **Nikos.Alexandris said:**
> Now, I bootet with Ubuntu 64-bit. It seems that the description in [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) is a bit different from your recomendation(?). Or does it not make any big difference (that is: partition-ing with BootCamp everything  or  just have free space and partition-ing with gparted). I already followed the steps described in previous link -- so I have to go through this.No, if you want to have other additional partitions other than your root partition and a swap, then please manually partition how you like. I was just showing the "easy" way to install.

> **Nikos.Alexandris said:**
> I will go ahead and try the XFS filesystem. Is it a bad idea?IDK that there are many that have tried. Can GRUB read the files (the kernel) from XFS?

> **Nikos.Alexandris said:**
> So, if I get it right there is now way to have more than 4 partitions?

One is the OSX and another one the EFI. I would like to split Linux in "/", "/home" and "swap", that is another 3 partitions. Or should I just forget the idea... ?

Any help highly appreciated, Nikos
No, you are misunderstanding. The actual root partition has to be one of the first 4 (or the /boot partition if you separate it out). GRUB uses the MBR partition table to boot, so it can only 'see' the four partitions contained there (and the Macs emulated MBR does not support extended and logical partitions). The Linux kernel, however, supports the GPT (the real partition table) so once the kernel is loaded, it doesn't matter what partitions there are, it can access any of them. So go ahead and create the separate home partition, just make sure the /boot folder will end up in the 4 'primary' partitions

---

### Post by Nikos.Alexandris on 2008-11-04
I like Ubuntu :-) I am surfing and doing other stuff while the install process is running!

So, you are right I think. With XFS I got a warning message that GRUB hangs when on XFS. So I created an ext3.

Installation complete... rebooting with rEFIt (I suppose), do the rEFIt magick and then hopefully all is ok.

Thnanks!

---

### Post by Nikos.Alexandris on 2008-11-04
(sorry for the double post -- don't know why firefox was taking too long...)

So, here I am. It works :D

Of course I booted by pressing "alt" and selecting the Windows hard disk icon.

Now I am starting testing...

---

### Post by Nikos.Alexandris on 2008-11-04
So far everything is like the [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) states.

But, I don't experience (always) a hang when shuting-down. What can I test? The other thread is full with posts inculding various commands/scripts. I am ready to give some feedback.

Cheers!

---

### Post by Nikos.Alexandris on 2008-11-05
Did somebody *really* try to transfer per Bluetooth any data on another computer or on a cell phone?

---

### Post by Nikos.Alexandris on 2008-12-05
Folks,

Great News: **the brightness keys**, that is the F(n)1 and F(n)2 keys, **work** in MBP5,1. I've just activated the 3D-effects, shut-down, (re)booted and... voila :D

I don't know whom I should thank about that. Please try and let me know (if you would like me to post any details).

Cheers, Nikos

---

### Post by Tyrannosaurus Rex on 2009-11-21
Using MBP 5,1 and I got Ubuntu 9.10 running fine, a few things to note that don't work (at all)

1 : Screen brightness keys
2 : Volume control keys (media keys like play and stuff do work)


WIRELESS IS WORKING (finally)

---

### Post by Nikos.Alexandris on 2009-11-22
> **Tyrannosaurus Rex said:**
> Using MBP 5,1 and I got Ubuntu 9.10 running fine, a few things to note that don't work (at all)

1 : Screen brightness keys
2 : Volume control keys (media keys like play and stuff do work)


WIRELESS IS WORKING (finally)

This is a very old thread. Both of the above do work. Just install "pommed".

---

