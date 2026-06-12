---
title: "USB Wireless Connection"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by weegie on 2008-01-31
Apologies for the long post but I don't have anywhere to store files for viewing online.
I am new to linux and ubuntu.

My problem is that I m trying to connect to a LAN using a Sitecom wl-012 wireless adapter.
It seems to be recognised but not configured. Can anyone help?

I am using Ubuntu edgy 6.10 on a Pentium 4, 2.8 Ghz desktop.
Dual boot with Windows XP on same disk. 
Adapter works without problems with Windows XP.

This is what I get using lsusb, iwconfig and lshw .(Only data that seems to be the relevant usb is posted --  to keep post short!)


mycomp@mycomp-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 050d:0841 Belkin Components 
Bus 003 Device 002: ID 0451:2077 Texas Instruments, Inc. TUSB2077 Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

mycomp@mycomp-desktop:~$ mycomp@mycomp-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

mycomp@mycomp-desktop:~$ sudo ifconfig wlan0 up
Password:
SIOCSIFFLAGS: No such device
mycomp@mycomp-desktop:~$ sudo lshw

      resources: ioport:bc00-bcff ioport:c000-c07f irq:225
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e0520000-e0520fff irq:177
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e0521000-e0521fff irq:185
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Prism 2.x 802.11b Adapter
                   vendor: Intersil Corp.
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.32
                   serial: 01310007
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e0522000-e0522fff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s


     
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes
mycomp@mycomp-desktop:~$

---

### Post by jrothwell97 on 2008-01-31
WLAN is notoriously patchy in Ubuntu, but it's improved greatly with Feisty and Gutsy. Therefore you might like to try upgrading to Gutsy: this is possible by burning the alternate install CD, and (I believe) setting it as a repository in Ubuntu. Try looking on the wiki, that might have more info.

---

### Post by benfindlay on 2008-01-31
Have you tried ndiswrapper to get the drivers working?

If not do the following:

First of all put your windows wifi drivers (off the cd that came with the adapter) somewhere accessable. For example create a desktop folder for them called wifi

for ndiswrapper type the following into command line a line at a time:

```
sudo apt-get install ndiswrapper-utils-1.9
```

```
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
```
 (perhaps /home/USERNAME/Desktop/wifi if you used my example)
```
sudo ndiswrapper -l
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -m
```
```
gksudo gedit /etc/modules
```

This opens a text eidtor
Click at the end of the list and type
```
ndiswrapper
```

Save and close. Then reboot

All should be well!

Hope this hepls!

---

### Post by OffAxis on 2008-01-31
There's also the community docs if ndiswrapper doesn't work for you.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by weegie on 2008-02-03
Thanks everyonefor your suggestions  but so far no success. I updraded to Gutsy 7.10 and have searched the wireless help documentation.

Also tried to find ndiswrapper on the live cd but it's not there and without internet access I cannot download and install.

Still persevering,.... trying to edit config fiels and so on .

---

### Post by benfindlay on 2008-02-03
If you go to [packages.ubuntu.com]("packages.ubuntu.com") and search for the relevent packages (i.e. ndiswrapper) it will allow you to download them on another computer, then transfer them via cd or pen driv to your ubuntu computer, thus getting round the wifi issue. The page for ndiswrapper will also list any repositories that you need to install before installing ndiswrapper.

Hope this helps!

---

### Post by polmir on 2008-02-03
Try this
[http://ubuntuforums.org/showpost.php?p=679465&postcount=1]("http://ubuntuforums.org/showpost.php?p=679465&postcount=1")

---

### Post by weegie on 2008-02-07
Once again thanks to everybody. I found out that ndiswrapper and linux-wlan-ng are both installed at boot in Gutsy 7.10. However still can't get connection with either option. Checking the dmesg log gives the following, so it seems that the drivers are not being initiated after loading. I am now checking the HW configuration of my machine.

dmesg output (partial)

[   25.095790] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver 
[   25.342006] prism2usb_init: prism2_usb.o: 0.2.8 Loaded 
[   25.342011] prism2usb_init: dev_info is: prism2_usb 
[   25.342308] usbcore: registered new interface driver prism2_usb 
[   25.400116] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23 
[   25.720510] intel8x0_measure_ac97_clock: measured 52715 usecs 
[   25.720516] intel8x0: clocking to 48000 
[   26.672346] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed) 
[   26.673330] hfa384x_drvr_start: cmd_initialize() failed, result=-5 
[   26.673335] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5 
[   27.412203] lp0: using parport0 (interrupt-driven). 
[   27.483634] ndiswrapper version 1.45 loaded (smp=yes) 
[   27.687589] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed) 
[   27.688576] hfa384x_drvr_start: cmd_initialize() failed, result=-5 
[   27.688580] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5 
[   27.763641] usbcore: registered new interface driver ndiswrapper 
[   27.867353] Adding 2048276k swap on /dev/sda4.  Priority:-1 extents:1 across:2048276k 
[   28.190677] EXT3 FS on sda2, internal journal 
[   28.611845] kjournald starting.  Commit interval 5 seconds 
[   28.612001] EXT3 FS on sda3, internal journal 
[   28.612008] EXT3-fs: mounted filesystem with ordered data mode. 
[   28.955046] NET: Registered protocol family 17

---

### Post by benfindlay on 2008-02-07
Just out of interest, what happens if you type ```
sudo ndiswrapper -l
``` into terminal. Is both the driver and the hardware present?

---

### Post by weegie on 2008-02-07
Ben,

ndiswrapper -l 
gives

mycomp@mycomp-desktop:~$ sudo ndiswrapper -l
[sudo] password for mycomp:
oemsetup : invalid driver!
wlannic : invalid driver!
mycomp@mycomp-desktop:~$ 

The oemsetup and wlannic files are the INF files found on the Sitecom driver disk. There are also SYS files but I don't know whether or how to include them in Ubuntu.

Thanks for your help,

---

### Post by benfindlay on 2008-02-07
Therein lies your problem! First of all lets remove the 2 invalid drivers. Launch a terminal and type ```
sudo ndiswrapper -r oemsetup
``` and
```
sudo ndiswrapper -r wlannic
```

Once you've done this, type ```
sudo ndiswrapper -l
``` again just to make sure there are no invalid conflicts still present

I would recommend looking around for any other .inf files found on the CD. Normally they have a name that relates to your specific piece of hardware. Alternatively, go to the manufacturer's website and try and download the specific drivers for your hardware. N.B. Get the XP version of the drivers if given a choice of a few.

Once you have these, your best bet is to go through the whole procedure of installing them again from scratch (starting AFTER sudo apt-get install ndiswrapper-utils-1.9 in the original list of instructions I posted earlier).

If that still doesn't work, then those are the wrong drivers for ubuntu then, despite the fact that they work in windows. What you need to do is determine which generic drivers will work with your specific hardware. Based on your lsusb post, its a > Intersil Corp. Prism 2.x 802.11b Adapter driver that you're looking for. A generic PRISM 2 chipset may work well, also, the Realtek 8180 drivers are very good at working with many wifi cards on linux. But try the prism 2 drivers first!

Hope this helps!

---

### Post by weegie on 2008-02-10
Thanks. Managed to install drivers OK but still no connection.

**lshw shows:**

 *-network DISABLED
       description: Ethernet interface
       physical id: 1
logical name: wlan0
capabilities: ethernet physical
configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.8 
link=no multicast=yes

**ndiswrapper -l  shows:**

mycomp@mycomp-desktop:~$ sudo ndiswrapper -l
[sudo] password for mycomp:
wlannic : driver installed
        device (09AA:3642) present (alternate driver: prism2_usb)
mycomp@mycomp-desktop:~$ 

Also** Network Manager **identifies the wireless card as a wired ethernet connection.

Somehow or other Ubuntu is not able to initiated the card although recognising it and having the correct drivers installed.

---

### Post by weegie on 2008-02-16
Problem solved! 

Not quite sure how but a complete reinstall of the Prism2 drivers and a few changes made to modprobe.d and wlan.conf seems to have worked. Ubuntu is now fully connected and it is well worth the effort.

Thanks to all who helped.

---

