---
title: "Compile! Getting a Realtek 8187 Wireless USB modem to work"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-14
I didn't even think this would be possible (and maybe it's not), but I plugged my Realtek 8187 USB modem into the old G4's USB port and started it up; when I typed lsusb in the terminal it showed up: 

Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

Then I idly opened the Synaptic Package Manager and typed in Realtek and here I see this :

[B][SIZE="3"]rtl8187se-source[/SIZE]

Realtek's rtl8187se driver allows 8187SE based board to work with the Linux
kernel

This package contains the module source. The kernel driver can be built from
it using module-assistant or make-kpkg.[/B]

Now, my problem is that I'm a Mac user; I have just started using Ubuntu and have virtually no serious linux experience; I've never compiled anything in my life and don't know where to start. So what I really need is a link to a site or wiki that will tell me about the process, 'cause it would be just too cool if I could get this to work.

This is a G4 Sawtooth (AGP Graphics) under Ubuntu 9.04. It has a USB 2.0 card.

---

### Post by stream303 on 2009-05-15
If you mean a wireless usb stick with the realtek 8187 chipset you are in luck.  Jaunty supports it natively without you having to compile anything.

My Netgear WG111v2 usb wireless works just fine out of the box with Ubuntu and Network Manager, including wpa2.  Makes a nice alternative to an airport express card - however, I have only been able to obtain 1mb speeds from it.

Since I just use it to surf the net, and not do any wireless streaming or file transfers, the speed is more than acceptable since my dsl speed hovers near 1mb anyway.

Try to bring it up in your KDE wireless configuration.

---

### Post by Benboom on 2009-05-15
**[COLOR="Red"]UPDATE:[/COLOR]** 

It's working now. I don't know why. :D Suddenly, it appeared in my network icon pulldown and I was able to enter the encryption key and my password and it connected right away.

I wish I knew what I did to make this happen! 'Cause I bet it will happen again...well, maybe I'll figure it out then. :D

----------------------

>If you mean a wireless usb stick with the realtek 8187 chipset you are in luck. Jaunty supports it natively without you having to compile anything.

That was my first thought when I saw it in the lsub window, but trying to get the wireless to actually work has been impossible so far so I thought it must be a driver issue. In light of your post this must be due to my comparative ignorance of how to configure the Ubuntu Network Settings. I don't have the KDE Wireless Config proram, but I assume the Ubuntu one has the same options in it. I'll have to find a primer on how to set it up; on the Mac the config program for the Realtek is simple (although very poorly written ergonomically) and there are only a couple of options as I assume it grabs info from my Mac Network prefs. However even while running thoe to compare with the Ubuntu version the options seem radically different.

1 MB is slower than my DSL modem/router, but not much (1.5 MB). I don't have fast broadband.

Update: I have found a couple of threads with people on PPCs having problems with wireless Ubuntu and I've tried lspci and iwconfig and it seems like the system doesn't recognize the USB stick. "No wireless extensions" is what I get across the board. The only hint that I have such a device is the output from lsusb, which Imentioned earlier.

Update 2: searching more threads I found the lshw command and got this, but I don't know if it's helpful:

lshw -C network
  *-network               
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:21:0f.0
       logical name: eth0
       version: 01
       serial: 00:30:65:7a:40:0a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=sungem driverversion=0.98 latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes
  [B]*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:0c:00:1c:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B]
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:15:e5:c1:24:dc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

----------

Another update:

After reading more threads I tried this and got:

nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             connected
  Default:           yes
  HW Address:        00:30:65:7A:40:0A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             192.168.1.254


[B]- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             disconnected
  Default:           no
  HW Address:        00:40:0C:00:1C:A1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE019:        Infra, 00:12:88:D3:FE:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 23 WEP
[/B]

(I don't think the console output is really supposed to have a smiley in it. :D) That's a : and a D

-----------

Another output; it seems like the machine is seeing the router through the wireless USB stick but I can't figure out how to get any further:

sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:12:88:D3:FE:89
                    ESSID:"2WIRE019"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/100  Signal level:65/65  
                    Encryption key:on
                    IE: Unknown: 00083257495245303139
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0102
                    IE: Unknown: 3205243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000016e542b82b
                    Extra: Last beacon: 2460ms ago

---------------

---

