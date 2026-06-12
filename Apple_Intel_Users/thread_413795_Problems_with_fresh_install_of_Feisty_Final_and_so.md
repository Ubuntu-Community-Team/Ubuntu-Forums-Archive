---
title: "Problems with fresh install of Feisty Final and solutions"
date: 2007-04-19
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-04-19
These are the issues on a fresh install of Feisty (final) on a MB C2D:
- When i use keyboard or apple remote to mute, turn up or turn down volume they don't work (the don't be associated to any sound card). To solve it you have to go to System/Preferences/Sound and down, select PCM  ;)
- Built-in iSight works by default but you have to go to System/Preferences/"Multimedia Selector" and choose for video input V4L2 and iSight :)
- When i write and in the same moment (or one second later) i use a USB mouse it don't worl :@ and i don't know how to solve it
- When i use custom keys with apple remote (like in kaffeine or amarok - i use ubuntu -) i cannot use this keys, and i have tried it a lot, but none

- And the worst (i had it in beta also): A lot of times, when i am writing i have problems, i mean, in example... i have firefox and terminal opened and if i am writing in firefox,  some times (a lot) the window changes to terminal..... :S   i don  :'('t use ubuntu so, because i cannot use OpenOFfice or other applications   :'(

Sorry for my poor english knowledge.

---

### Post by ronocdh on 2007-04-19
> - And the worst (i had it in beta also): A lot of times, when i am writing i have problems, i mean, in example... i have firefox and terminal opened and if i am writing in firefox, some times (a lot) the window changes to terminal..... :S i don :'('t use ubuntu so, because i cannot use OpenOFfice or other applications :'(
This was the only part of the post I didn't understand. (Your English is remarkably clear!) [LIST=1]
[*]Why can't you use Open Office in Ubuntu? Is that what you meant?
[*]Are you sure that the application change isn't a touchpad-related issue? I have often had the problem of an overly sensitive touchpad, and while I typed my thumbs barely grazed the touchpad surface, which caused cursor motion and/or a click. If the cursor was anywhere near the Gnome menu bar, it could have switch applications this way.
[/LIST]Just my thoughts! Great news on the iSight, btw... thanks for posting that. Hopefully someone has an xorg.conf fix for the USB mouse problem?

---

### Post by mustang on 2007-04-19
> **Azathoth_ said:**
> These are the issues on a fresh install of Feisty (final) on a MB C2D:
- When i use keyboard or apple remote to mute, turn up or turn down volume they don't work (the don't be associated to any sound card). To solve it you have to go to System/Preferences/Sound and down, select PCM  ;)


I'm encountering this on my core duo macbook as well. It's listed as a bug on launchpad. While I don't know the solution, one solution might be to use a keygrabber like xmodmap and reroute those keys to + and - PCM. 

> 
- When i write and in the same moment (or one second later) i use a USB mouse it don't worl :@ and i don't know how to solve it


Not sure what you mean here. Can you rephrase this for us?

> 
- And the worst (i had it in beta also): A lot of times, when i am writing i have problems, i mean, in example... i have firefox and terminal opened and if i am writing in firefox,  some times (a lot) the window changes to terminal..... :S   i don  :'('t use ubuntu so, because i cannot use OpenOFfice or other applications   :'(


My guess as to the cause would be your accidentally touching the touchpad when typing. What you can do is use gsynaptics to disable the touchpad when your mouse is connected.

---

### Post by Azathoth_ on 2007-04-19
> **mustang said:**
> I'm encountering this on my core duo macbook as well. It's listed as a bug on launchpad. While I don't know the solution, one solution might be to use a keygrabber like xmodmap and reroute those keys to + and - PCM. 

I thought it, but i prefer a fix before rerouting xmodmap


> **mustang said:**
> Not sure what you mean here. Can you rephrase this for us?

Sorry, i tried to say that, if i'm pressing any key, at the same time i cannot use my USB mouse, it stops even if i move it.


> **mustang said:**
> My guess as to the cause would be your accidentally touching the touchpad when typing. What you can do is use gsynaptics to disable the touchpad when your mouse is connected.

Yes, i will try it in a few minutes, thanks

---

### Post by wootwoot123 on 2007-04-19
I didn't see you mention wireless. Does that mean that wireless worked out of the box? I want to install this today but worry about the wireless portion. I messed up my wifi after upgrading to some of the betas so I am going to do a fresh install today.

---

### Post by Azathoth_ on 2007-04-19
If you have airport extreme, wireless doesn't work by default, because AR5008 chipset is still in developmet en madwifi-hal

You can use ndiswrapper ;)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by bsantos on 2007-04-20
iSight works on a fresh install? Why would it fail otherwise, what kernel are you using?

Which is the device id of yours? 05ac:8501?

---

### Post by Azathoth_ on 2007-04-21
I'm using 2.6.20-15-generic
It works by default as i said before ;)

---

### Post by mustang on 2007-04-21
> **Azathoth_ said:**
> I thought it, but i prefer a fix before rerouting xmodmap


Just realized you can go to System->Preferences->Sound and select "PCM" for the default mixer track. No xmodmap needed :)

---

### Post by paulo_ on 2007-04-21
> **Azathoth_ said:**
> I'm using 2.6.20-15-generic
It works by default as i said before ;)

Working by default? Well, not for me... No iSight :\

[IMG]http://img253.imageshack.us/img253/8472/screenshotmultimediasysns1.png[/IMG]

---

### Post by bsantos on 2007-04-21
I've rearranged my partitions to give more room to Linux and took the chance to reinstall it. Still no luck with iSight. :(

You're on a Core 2 Duo also?

---

### Post by paulo_ on 2007-04-21
No. Intel Core Duo.

---

### Post by bsantos on 2007-04-22
Aha! :)

We're out of luck for now...

---

### Post by Azathoth_ on 2007-04-22
Try to compile linux-uvc

---

### Post by bsantos on 2007-04-22
I tried to compile uvc, and still nothing.

Can you post your lsusb -v for the iSight?

```

Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x8501 
  bcdDevice            1.84
  iManufacturer           1 Micron
  iProduct                2 Built-in iSight
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          267
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    UNRECOGNIZED:  08 24 00 02 ff ff ff 00
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by Azathoth_ on 2007-04-22
Yes, here you are.

---

### Post by bsantos on 2007-04-22
Core Duo:
Bus 005 Device 008: ID 05ac:8501 Apple Computer, Inc. 

Core 2 Duo:
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. 


That's the only difference, the main stuff like the ID is the same, what can be wrong? :(

---

### Post by bsantos on 2007-04-22
T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=05ac ProdID=8501 Rev= 1.84
S:  Manufacturer=Micron
S:  Product=Built-in iSight
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=64ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=05(Isoc) MxPS=3072 Ivl=125us

The module is loaded but Driver=(none)... Can you check your /proc/bus/usb/devices? :)

---

### Post by bsantos on 2007-04-22
Patch for latest svn:
[http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/)

---

