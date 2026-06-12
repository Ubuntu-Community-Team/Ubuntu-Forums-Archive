---
title: "Ativa Wireless USB setup on Xubuntu 7.04"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Nimaran on 2007-06-27
Hello,

I am very new to Linux, but I have managed to install Xubuntu 7.04 and I would like to get my wireless internet working. I have an Ativa Wireless G USB Adapter. So for now I''m in Windows writing this post. Anyone who can help me get this working it would be greatly appreciated. I don't know if I just need  a driver or what, but I'm willing to try Linux, but one has to have an internet connection to do anything in Linux.

Thanks in advance,

-Nimaran

---

### Post by amsterdam on 2007-06-27
Try running this at a terminal:

     lspci

It should return several lines. Look for something that resembles a wireless card, mine looks like this for example:
      02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by Nimaran on 2007-06-28
Posted at the bottom is what it gave me among a long list of other components, and I managed to find the network manager device, so if Xubuntu recognizes my USB wireless all I should have to do is fill in the proper info, right?

Oh, and I realized another problem. On the particular network I need working a device is in place called a D-Link Secure Spot, and in order to use the network the thin client is installed, but I don't know if their is one for Linux, is it possible to somehow copy or run the windows version?


01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by RanulfWolfSage on 2007-06-28
I'm probably not the best person to be throwing out advice as I'm rather new to Linux, but I managed to get my wireless G PC-Card functioning on my Ubuntu laptop by following the info on this site:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html")

I hope it helps!

---

### Post by amsterdam on 2007-06-28
> **Nimaran said:**
> 01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

That is the wired connection, not the wireless. It seems the card is not installed. Check out the post from the other user, it may point you in the right direction.

I do not know how the live CD handles adding devices. If you doing all this through the live CD, it could be the root of the issue.

Keep us posted.

---

### Post by Nimaran on 2007-06-29
No, I have installed it on my hard drive. I am not running it through the live cd. I'll check out that other forum, but here is all the results that command gave me. Is it somewhere in there?



00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
01:05.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by amsterdam on 2007-06-29
I dont think it is listed. If i remember, installing a wireless driver (madwifi, whatever...) is a bit complicated especialy for people who are not experts in linux (like myself). 

Neverless, I say try and installing it via the last post. Let us know what you have done and the results even if you did get it working to help those in the future with a similar setup.

---

### Post by Nimaran on 2007-06-29
Ok, I'll try that thanks, except now something else isn't working. I can't even acess linux if you have any ideas check out my post entitled Xubuntu Session Start.

---

### Post by ugm6hr on 2007-06-29
If the wireless is a USB card - you need:
```
lsusb
```
This will list the USB ID for it.

Quick search on your behalf revealed these:
[http://bsdimp.blogspot.com/2007/05/ativa-wireless-g-network-adapter.html](http://bsdimp.blogspot.com/2007/05/ativa-wireless-g-network-adapter.html)
[http://www.linuxwireless.org/en/users/Drivers/zd1211rw](http://www.linuxwireless.org/en/users/Drivers/zd1211rw)

Between them, they suggest that your USB adapter should just work with kernal 2.6.18, but that means you need some way to connect to the internet to update the 7.04 kernel.

Good luck.

---

### Post by Nimaran on 2007-06-29
Thank you guys for all your help I'll try your suggestions once I can get everything else working. This forum is great and you guys are great. I post a question and it's like live support, with the whole community out there willing to help. Thank you.

---

### Post by Nimaran on 2007-06-29
What do you mean by update my kernel? I am running the 7.04 of Xubuntu, or is it something else I have to update.

---

### Post by ugm6hr on 2007-06-30
> **Nimaran said:**
> What do you mean by update my kernel? I am running the 7.04 of Xubuntu, or is it something else I have to update.

My mistake - I think Xubuntu7.04 has a 2.6.20 kernel, so it should work (in theory), provided the USB ID is in the supported list (check *lsusb*):
[http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices)

If not....
There is a link to how to add IDs to the driver:
[http://www.linuxwireless.org/en/users/Drivers/zd1211rw/AddID](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/AddID)
I'm not sure if you will have to compile your own kernel to do this:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Nimaran on 2007-07-01
Wait, this seems to be talking about something with firmware. Will I have to put diffrent firmware on it? If I do will I still be able to use the same card under Windows XP?

---

### Post by ugm6hr on 2007-07-01
> **Nimaran said:**
> Wait, this seems to be talking about something with firmware. Will I have to put diffrent firmware on it? If I do will I still be able to use the same card under Windows XP?
I haven't had a good read of it myself, but I don't think it requires a firmware update.  

But best to start by typing the following in Terminal and letting us know what it says:
```
lsusb
```

---

### Post by Nimaran on 2007-07-01
Among my other USB devices it gives me this:

Bus 004 Device 002: ID 050d: 705c Belkin Components

---

### Post by ugm6hr on 2007-07-01
That is already in the supported list:
Belkin  	F5D7050 v.4000  	zd1211b  	050d  	705c  	AL2230

So changing the USB ID won't help.  But it does suggest that it should be possible to get it to work.  Unfortunately, I don't know how.

I'm afraid to give any further advice on this, since I've never used this driver.  It also makes specific mention of Debian-based distros having problems.  Maybe try the IRC channel mentioned for further help (IRC: Freenode, #zd1211).

EDIT:
Ndiswrapper looks like it sort of works (as an alternative) - look at Number 15 here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

EDIT2:
This purports to be a solution (for Edgy - but worth a look):
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)
Written by FrodoB: [http://ubuntuforums.org/showthread.php?t=295843&highlight=F5D7050+4000](http://ubuntuforums.org/showthread.php?t=295843&highlight=F5D7050+4000)

Good luck with this.

---

### Post by Nimaran on 2007-07-01
I went to that link and got these instructions I have the wrapper and ran it for the .inf file in the directory although its named something different. Ho do I find where to put the .sys? Also, what do I do from there?


Card: Belkin Wireless G USB Network Adapter

    *
      Chipset: Unsure
    *
      usbid: 050d:705c
    *
      Driver: On the CD at /files/Driver/blkwgu.inf
    *
      Other: run ndiswrapper -i blkwgu.inf on CD, copy blkwgu.sys to same directory as ndiswrapper puts the inf file. bring up device. Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch, pretty straightforward.

---

### Post by ugm6hr on 2007-07-02
Unfortunately, Xubuntu doesn't have a default search for files function, but from memory, ndiswrapper puts the driver it in* /etc/ndiswrapper*, so just copy the .sys file there.

If the driver on your CD doesn't work, this is probably a good place to get the Belkin driver from:
[http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221&fid=2767&fn=F5D7050v4.exe](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221&fid=2767&fn=F5D7050v4.exe)
If you extract it in Windows, it should have both .inf and .sys files (hopefully).

Most people would argue that the native Linux solution (EDIT2) is theoretically better (doesn't involve Windows drivers), but I suppose what's important is that it works....

This is useful as a ndiswrapper how-to:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

This has a how-to for compiling the latest ndiswrapper (which I believe is necessary if you want WPA):
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29#head-5f3185a84cd49ce95d0342c33ffcb41df3a7fc79](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29#head-5f3185a84cd49ce95d0342c33ffcb41df3a7fc79)

---

### Post by ugm6hr on 2007-07-02
Another post that claims to have solved the issue:
[http://ubuntuforums.org/showthread.php?p=2951142#post2951142](http://ubuntuforums.org/showthread.php?p=2951142#post2951142)

---

### Post by Nimaran on 2007-07-02
The NDISWrapper how-to seems like it will help, but it seem to be built for PCI cards will it work for USB if I just change the lspci to lsusb?

---

### Post by ugm6hr on 2007-07-02
> **Nimaran said:**
> The NDISWrapper how-to seems like it will help, but it seem to be built for PCI cards will it work for USB if I just change the lspci to lsusb?

The lspci reference in that how-to is merely there to find out which driver you need to use.  You have already done the equivalent with lsusb - so you can skip 2.5 steps 1-6.  Use either the driver on your CD (or probable better to use the one I linked to).

---

### Post by Nimaran on 2007-07-02
I donloaded the driver you said. I then extracted it to my USB flash drive. I'm in Windows right now and I don't see a .sys or .inf file.

---

### Post by ugm6hr on 2007-07-02
> **Nimaran said:**
> I donloaded the driver you said. I then extracted it to my USB flash drive. I'm in Windows right now and I don't see a .sys or .inf file.

Really?  I'm not sure how it can be a Windows driver without a .inf file...  

Make sure you have selected to view hidden files, just to be certain.  

If there is another .exe file in there, it may be that it requires you to install the driver on a Windows PC to create the .inf file, but I'm not sure...

If it's not easily accessible, probably best to just try the .inf / .sys files on your CD.

PS: I will try and have a look at the driver file myself when I next boot into Windows.  Unfortunately, that's generally only every 2 weeks or so...

---

### Post by Nimaran on 2007-07-02
Even though I installed it on my flash drive, could it have put some other files (.inf, .sys) on my hard drive. Just possible is what Windows labels as a configuration file a .sys or .inf files. IN other words could it be denoted as a different file type in Windows?

---

### Post by ugm6hr on 2007-07-02
> **Nimaran said:**
> Even though I installed it on my flash drive, could it have put some other files (.inf, .sys) on my hard drive. Just possible is what Windows labels as a configuration file a .sys or .inf files. IN other words could it be denoted as a different file type in Windows?
Possibly - try searching for *blkwgu.inf* on Windows (assuming that ndiswrapper has the correct name).

PS: It will be a hidden file in Windows.
What files did it extract to the USB?

---

### Post by Nimaran on 2007-07-02
You want me to list all of them? There is a lot.

---

### Post by Nimaran on 2007-07-02
Ok. For now I decided to go with the driver on my CD. I opened NDISWrapper and got the .inf files and all of that. The view on the left has it show up, but is says Hardware Present: No. I also typed the command the Wrapper help gave me to check if it was installed correctly. This is what it gave me. Any suggestions?

odwgu : driver installed
        device (050D:705C) present (alternate driver: zd1211rw)

---

### Post by ugm6hr on 2007-07-03
Because the "native" Linux driver for your wifi card is *zd1211rw*, step 2.4 needs to be done like this:
```
echo 'blacklist zd1211rw' | sudo tee -a /etc/modprobe.d/blacklist
```
Then try again.  

PS: Remember to make a copy / backup of the following file first:
```
/etc/modprobe.d/blacklist
```
The command above is supposed to edit it for you.

---

### Post by Nimaran on 2007-07-03
I tried what you said,  and I am posting the outputs for various commands.

I get this when I type: 
sudo ifdown wlan0
  sudo ifup wlan0


seth@seth-desktop:~$  sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3961
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:1d:47:81
Sending on   LPF/wlan0/00:17:3f:1d:47:81
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
seth@seth-desktop:~$   sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:1d:47:81
Sending on   LPF/wlan0/00:17:3f:1d:47:81
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 964012412 seconds.


I get this when I type:
ndiswrapper -l

odwgu : driver installed
        device (050D:705C) present (alternate driver: zd1211rw)
system : invalid driver!

I get this when I type:
tail /var/log/messages

Jul  3 09:39:01 seth-desktop kernel: [   42.864662] apm: overridden by ACPI.
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): starting (version 2.18.0.1), pid 5069 user 'seth'
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): Resolved address "xml:readwrite:/home/seth/.gconf" to a writable configuration source at position 1
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  3 09:39:09 seth-desktop gconfd (seth-5069): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  3 09:44:25 seth-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul  3 09:58:34 seth-desktop -- MARK --
Jul  3 10:00:31 seth-desktop kernel: [ 1353.519322] wlan0: duplicate address detected!


(I still think something isn't working. Do these outputs give any insight?)

---

### Post by Nimaran on 2007-07-03
Yeah!! I got it working, but please don't ask me how, because I have no earthly idea. I started following the instruction on one of those web pages, and bam it worked.

But of course, now I have another problem. Attached to the network I need to connect to is a device called a D-Link Securespot, and in order to access the internet you need a thin client to be installed. Now, I downloaded both the Mac and the Windows version of it. The Mac looks like some kin =d of Linux-like archive which is good, but I have no idea how to use it. The Windows one I installed via Wine, and it is installed, but I still can't access the Internet. I don't know how to make Wine "use it" or if I am missing something. You have been a great help, and I would love it if you could assist me with this one last problem. Thank you so much you have been great.

---

### Post by ugm6hr on 2007-07-03
Glad you got it working - might be nice to let future forum searchers know which thread you used to get it working...

As for the D-Link Securespot issue... maybe try searching or reposting in the hardware forum.  Sorry, can't help with that.

---

### Post by Tommy Boy on 2008-01-20
I just installed Ubuntu 7.10and had the wireless usb dongle plugged in when Iinstalled it and it worked immediately. I am a really fresh n00b to linux so this is all I can offer. I hope this helps you.:)

---

