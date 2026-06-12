---
title: "Ubuntu on Macbook Pro '08"
date: 2008-02-27
forum: Apple Intel Users
---

### Post by tannewt on 2008-02-27
Hi all,
I just got a new Macbook Pro today and am beginning to embark on getting Linux running on it in addition to OS X.  Here are some of the specs:

> Hardware:

    Hardware Overview:

      Model Name: MacBook Pro
      Model Identifier: MacBookPro4,1
      Processor Name: Intel Core 2 Duo
      Processor Speed: 2.4 GHz
      Number Of Processors: 1
      Total Number Of Cores: 2
      L2 Cache: 3 MB
      Memory: 2 GB
      Bus Speed: 800 MHz
      Boot ROM Version: MBP41.00C1.B00
      SMC Version: 1.27f1
      Serial Number: W8808H59YJX
      Sudden Motion Sensor:
          State: Enabled

Audio (Built In):

    Intel High Definition Audio

Bluetooth:

      Apple Bluetooth Software Version: 2.1.0f16
      Hardware Settings:
              Manufacturer: Broadcom
              Firmware Version: 4.199 (4.8583)

Graphics/Displays:

    GeForce 8600M GT:

      Chipset Model: GeForce 8600M GT
      Type: Display
      Bus: PCIe
      PCIe Lane Width: x16
      VRAM (Total): 256 MB
      Vendor: NVIDIA (0x10de)
      Device ID: 0x0407
      Revision ID: 0x00a1
      ROM Revision: 3212
      Displays:
        Color LCD:
          Display Type: LCD
          Resolution: 1440 x 900
          Depth: 32-bit Color
          Built-In: Yes
          Core Image: Hardware Accelerated
          Main Display: Yes
          Mirror: Off
          Online: Yes
          Quartz Extreme: Supported
        Display Connector:
          Status: No display connected

So far I've download the amd64 version of Ubuntu 7.10, installed rEFIt and partitioned the drive leaving OS X 40 gb of the ~186.

My biggest concerns are getting the wireless working.  I spotted notes about a bcm43xx firmware in the system profile.  I'm also uncertain about the new fancy trackpad.  More will come later when I attempt to boot to the CD and eventually install it all.

---

### Post by gutsy08 on 2008-02-27
Congrats, good luck with the install!

---

### Post by cyberdork33 on 2008-02-27
> **tannewt said:**
> My biggest concerns are getting the wireless working.  I spotted notes about a bcm43xx firmware in the system profile.  I'm also uncertain about the new fancy trackpad.  More will come later when I attempt to boot to the CD and eventually install it all.

You have Broadcom Wi-Fi? That doesn't sound right. They have been using Atheros in Macbook Pros (Of course they did switch the Macbooks over to Broadcom in the last update). Either way, *IF* you have a Broadcom card, it is likely a 4328 card, and bcm43xx will not work (or any of the newer versions of it such as b43, etc). You have to use ndiswrapper.

Most everything should be close to that same as the previous edition:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by tannewt on 2008-02-27
Well, I have good news and bad news:

Bad: rEFIt doesn't work and I can only boot to livecd.
Good: the trackpad works with the livecd.

With some modifications of the livecds boot arguments I have a full desktop running.  I'm currently in the middle of the install.  Wireless doesn't though.

Sorry its brief I'm posting from my phone.

---

### Post by cyberdork33 on 2008-02-27
> **tannewt said:**
> Well, I have good news and bad news:

Bad: rEFIt doesn't work and I can only boot to livecd.
Good: the trackpad works with the livecd.

With some modifications of the livecds boot arguments I have a full desktop running.  I'm currently in the middle of the install.  Wireless doesn't though.

Sorry its brief I'm posting from my phone.
rEFIt often breaks on new hardware. It isn't a necessity anyway. There will probably be a new release soon if the devs can get some tech info.

Please post your boot args. Also, can you say what the hardware version number is now? (In system profiler I believe, and maybe in dmesg).

---

### Post by tannewt on 2008-02-27
When presented with the boot menu I:

1) Select 1440x900x32 in F4: VGA.
2) Start in Safe Graphics Mode.

Note that this is just how I got it working and you may not have to do 1.

The version for the machine I believe is 4,1.  I saw it in the dump I did but didn't save it and cannot access OS X at the moment.
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

Looks like it is Broadcom Wireless.

I've successfully installed it but cannot boot to it because rEFIt is not working.  I'm going to install grub because I skipped it originally.

I see that rEFIt had MacBookAir support added by a LegacyLoaderDevice path.  Any clue how I find that for my machine?

---

### Post by tannewt on 2008-02-27
Well, I installed GRUB and had to hand configure the menu.lst because it was poorly autogenerated.  So far I have booting into Ubuntu from hard disk working.  I'm still unable to boot to OS X.  Later I'm going to work on wireless drivers.

---

### Post by cyberdork33 on 2008-02-27
> **tannewt said:**
> When presented with the boot menu I:

1) Select 1440x900x32 in F4: VGA.
2) Start in Safe Graphics Mode.

Note that this is just how I got it working and you may not have to do 1.
I don't think you need to do 1 either.

> **tannewt said:**
>  The version for the machine I believe is 4,1. I saw it in the dump I did but didn't save it and cannot access OS X at the moment. It should also be in the beginning of your dmesg output I think.... It is in mine anyway.

> **tannewt said:**
>  I see that rEFIt had MacBookAir support added by a LegacyLoaderDevice path.  Any clue how I find that for my machine?You need to talk to the rEFIt guys. Open a bug report with them, and I am sure they will let you know what they need.

> **tannewt said:**
> Well, I installed GRUB and had to hand configure the menu.lst because it was poorly autogenerated.  So far I have booting into Ubuntu from hard disk working.  I'm still unable to boot to OS X.  Later I'm going to work on wireless drivers.You might have messed something up then. Installing Ubuntu should not prevent you from booting OS X. rEFIt isn't needed to switch, you just have to hold the Option key while starting up.

---

### Post by tannewt on 2008-02-28
Well, no luck with wireless.  Its a revision 5 card and I can't manage to get windows drivers files for it.

I did just get sound working by adding the snd_hda_intel model=mpb3 line.

More tomorrow.

---

### Post by amonsul on 2008-02-28
Im getting a new MAcbbokPro now so i rally hope to read some success story from you! :(


Good luck!
:)

---

### Post by cyberdork33 on 2008-02-28
> **tannewt said:**
> Well, no luck with wireless.  Its a revision 5 card and I can't manage to get windows drivers files for it.

I did just get sound working by adding the snd_hda_intel model=mpb3 line.

More tomorrow.
You can (painfully) extract drivers from the "driver cd" portion of the Leopard DVD that may work. Are you currently trying to use the Dell [R151517]("http://ftp.us.dell.com/network/R151517.EXE") driver?

---

### Post by tannewt on 2008-02-28
I got it!  I used the windows XP drivers off of the mac OS X CD 1 with ndiswrapper.  To extract the files from the exe I used 7-zip on a windows box.

---

### Post by cyberdork33 on 2008-02-28
well that's two for two today on ndiswrapper! Seems to be that the New Macbooks Pros and the Macbook Air need the driver on their respective discs.

---

### Post by tannewt on 2008-02-28
Now I'm working on getting the hotkeys working and exploring advanced touchpad capabilities.

I've found the usb device info for the HCI devices:

> Bus 005 Device 004: ID 05ac:0230 Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x0230 
  bcdDevice            0.70
  iManufacturer           1 Apple, Inc.
  iProduct                2 Apple Internal Keyboard / Trackpad
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              3 Apple Internal Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     156
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              4 Touchpad
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      27
          Report Descriptor: (length is 27)
            Item(Global): Usage Page, data= [ 0x00 0xff ] 65280
                            (null)
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Main  ): Collection, data= [ 0x03 ] 3
                            Report
            Item(Global): Usage Page, data= [ 0x00 0xff ] 65280
                            (null)
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Global): Report ID, data= [ 0x44 ] 68
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0xff 0x01 ] 511
            Item(Main  ): Input, data= [ 0x00 ] 0
                            Data Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              4 Touchpad
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
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

My guess is that the broadcom gesture chip is probably the touchpad that doesn't speak mouse.

---

### Post by tannewt on 2008-02-29
I got rEFIt working.  I'm not quite sure how actually.

I was messing around with trackpad stuff and booted into OS X via the install CD.  I then reinstalled rEFIt again and pulled up the partition manager utility also.  I then installed a new kernel thing for OS X and it prompted a restart.  While it was shutting down it told me it had to update the boot cache.  Once it was done with that upon startup it showed rEFIt and it works with booting both OS X and linux.

---

### Post by cyberdork33 on 2008-02-29
> **tannewt said:**
> I got rEFIt working.  I'm not quite sure how actually.

I was messing around with trackpad stuff and booted into OS X via the install CD.  I then reinstalled rEFIt again and pulled up the partition manager utility also.  I then installed a new kernel thing for OS X and it prompted a restart.  While it was shutting down it told me it had to update the boot cache.  Once it was done with that upon startup it showed rEFIt and it works with booting both OS X and linux.Did you use the automatic installer the first time? That has been known to not work in some instances. Installing manually (using the script in the package /efi/refit/enable.sh or something like that) usually gets it working correctly. I am not sure exactly what you did to get it working, but sharing that type of info with the refit developers will likely help them improve the software.

---

### Post by pravinbravi on 2008-04-29
> **cyberdork33 said:**
> You can (painfully) extract drivers from the "driver cd" portion of the Leopard DVD that may work. Are you currently trying to use the Dell [R151517]("http://ftp.us.dell.com/network/R151517.EXE") driver?
Ndiswrapper Dell R151517 don't work, use the one from your OS X DVD.

Also strangely the bcmxx drivers thru ndiswrapper do not work on 64bit ubuntu gutsy & hardy.

---

### Post by cyberdork33 on 2008-04-29
> **pravinbravi said:**
> Also strangely the bcmxx drivers thru ndiswrapper do not work on 64bit ubuntu gutsy & hardy.What do you mean by that? I use ndiswrapper under 64bit ubuntu just fine.

---

### Post by pravinbravi on 2008-06-22
For the wifi use ndiswrapper and most importantly, use the broadcom drivers from your boot camp CD. It doesn't work with amd64 tho sadly. So have to stick to 32bit.

Works absolutely fine with me.

--
Pravin

---

