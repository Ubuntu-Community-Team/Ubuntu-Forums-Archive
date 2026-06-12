---
title: "Close to giving up on Ubuntu..."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Blue Ocean on 2007-06-11
After the many many things that have pissed me off with XP, I recently decided to install Ubuntu (7.04), which I managed to do successfully as part of a dual-boot setup via Grub. 

However I have 1 major and another annoying problem:

I am a total noob when it comes to Linux - I was hoping I could use Linux for day to day use - music, videos, internet etc. This is all fine, but I have a Linksys WUSB54G wireless USB adapter which I can't get to work with the WPA encryption that is on my wireless network. (The network shows when I click the icon on the top right hand corner, but there is no 'WPA Personal' option in the drop down menu). 

I've followed various guides, which haven't worked for one reason or another. I have a feeling using ndiswrapper with my Windows drivers might work - however I have no idea how to install it/use it (all the guides seem too technical for me). The annoying thing is that I can't seem to play any of my music/videos without downloading appropriate codecs - which I can't do because I can't connect to the net. This completely defeats the purpose of my Ubuntu install!

My second problem - I can't seem to change my monitor refresh rate - its stuck at 72 or 76Hz I think, and I want to bring it down because it's causing the redrawing of windows to struggle. I have an integrated nVidia GeForce 4 MX Graphics card. When I go into the hardware drivers menu - it comes up with a driver for my graphics card which is unactivated. However, when I've tried many times to activate it, nothing happens. Eventually, I would like to install Beryl, and I'm pretty sure I need to get the driver to work before it'll let me do anything 3D. 

The plus side is that the resolution is fine at 1280x1024, although whenever I have just been using Windows and then decide to reboot in Ubuntu, the screen is shifted horizontally so that the right side is cut off - I have to keep readjusting my monitor settings to correct it.

Sorry about the problems but since Windows is doing what I need it to do and Ubuntu isn't at the moment, it's temping to reclaim my hard disk space back for XP!

Finally, if I do decide to get rid of Ubuntu, I don't have an XP CD but I have a recovery partition with XP on it which was setup when I bought the PC. How do I reset my original boot process (ie. remove grub) without the XP CD?

Thanks a bunch! I really do want to get Ubuntu to work!

---

### Post by eZtaR on 2007-06-11
[Here's](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html) a guide for getting wireless to work using ndiswrapper :) It's for the dell inspiron 1501 but you should get the idea :)

Apart from that i would recommend, granted that your wireless connection still doesn't work after fooling around with ndiswrapper, that you simply change your routers configuration from using WPA to using WEP (which in my point of view works better with linux).

---

### Post by Crafty Kisses on 2007-06-11
> **Blue Ocean said:**
> After the many many things that have pissed me off with XP, I recently decided to install Ubuntu (7.04), which I managed to do successfully as part of a dual-boot setup via Grub. 

However I have 1 major and another annoying problem:

I am a total noob when it comes to Linux - I was hoping I could use Linux for day to day use - music, videos, internet etc. This is all fine, but I have a Linksys WUSB54G wireless USB adapter which I can't get to work with the WPA encryption that is on my wireless network. (The network shows when I click the icon on the top right hand corner, but there is no 'WPA Personal' option in the drop down menu). 

I've followed various guides, which haven't worked for one reason or another. I have a feeling using ndiswrapper with my Windows drivers might work - however I have no idea how to install it/use it (all the guides seem too technical for me). The annoying thing is that I can't seem to play any of my music/videos without downloading appropriate codecs - which I can't do because I can't connect to the net. This completely defeats the purpose of my Ubuntu install!

My second problem - I can't seem to change my monitor refresh rate - its stuck at 72 or 76Hz I think, and I want to bring it down because it's causing the redrawing of windows to struggle. I have an integrated nVidia GeForce 4 MX Graphics card. When I go into the hardware drivers menu - it comes up with a driver for my graphics card which is unactivated. However, when I've tried many times to activate it, nothing happens. Eventually, I would like to install Beryl, and I'm pretty sure I need to get the driver to work before it'll let me do anything 3D. 

The plus side is that the resolution is fine at 1280x1024, although whenever I have just been using Windows and then decide to reboot in Ubuntu, the screen is shifted horizontally so that the right side is cut off - I have to keep readjusting my monitor settings to correct it.

Sorry about the problems but since Windows is doing what I need it to do and Ubuntu isn't at the moment, it's temping to reclaim my hard disk space back for XP!

Finally, if I do decide to get rid of Ubuntu, I don't have an XP CD but I have a recovery partition with XP on it which was setup when I bought the PC. How do I reset my original boot process (ie. remove grub) without the XP CD?

Thanks a bunch! I really do want to get Ubuntu to work!

For the codecs and everything else go to:

[http://getautomatix.com]("http://getautomatix.com")

That will automatically install ALL the codecs and everything you need, be warned it's not recommended by a lot of people but I've used it before and it works fine. :p

---

### Post by cwmoser on 2007-06-11
My suggestion is to perservere.  I have finally ridded myself of Windows on my home PC and I have found Ubuntu to be much faster and a better environment.  There is a learning curve but after a point it doesn't seem as much a struggle.

I'm running Ubuntu with QuickBooks, Quicken via CrossOver.  I've gotten VPN working, NXServer for remote access, ntfs-3g to access my windows paritions, been able clone my Linux partition, installed MonoDevelop and compiled some C++ programs using GTK++, and installed numerous apps.  It has been a rewarding learning experience and should enhance my resume.

HINT:  if you have video issues, get an nVidia card.  I was using an ATI but gave up on it and bought an nVidia GeForce 6200 for $75 on Ebay.  I've got Beryl running with dual monitors and that far exceeds the eye candy that Vista can produce.

Good luck.

Carl

---

### Post by Blue Ocean on 2007-06-11
> **eZtaR said:**
> 
Apart from that i would recommend, granted that your wireless connection still doesn't work after fooling around with ndiswrapper, that you simply change your routers configuration from using WPA to using WEP (which in my point of view works better with linux).

I know it does - however, seeing as WPA is more secure and it works on XP already, I don't see the value in moving to linux for security and stability but then sacrificing the security of my network. 

The guide looks helpful, so I'll give it a go - thanks for that.

---

### Post by ruialexbarbosa on 2007-06-11
I'm sorry but I have to be honest on this one:

You are pissed off with XP so you move to Ubuntu, a free alternative (which I'm using 99% of the time now, despite knowing next to nothing about Linux) and you want to give up because it's not a lot better than xp? If xp is so good, well, easy choice...

---

### Post by Wim Sturkenboom on 2007-06-11
With regards to the refreshrate:
edit /etc/X11/xorg.conf and add *Option "UseEdidFreqs" "false"* tot the device section; you need root permissions

Oops, did not read correctly. To bring it down, change the line with VertRefresh so the maximum is lower (put the above line in as well). Please note that that is more than likely not the cause of your redrawning problem.

And you can align your screen position in that config file as well. I will try to come back on that as well

---

### Post by umattu on 2007-06-11
> **Codename said:**
> For the codecs and everything else go to:

[http://getautomatix.com]("http://getautomatix.com")

That will automatically install ALL the codecs and everything you need, be warned it's not recommended by a lot of people but I've used it before and it works fine. :p


You dont even have to go that far, to install the codecs all youu need is like a .wmv file and put it on the desktop. Double click the file, ubuntu will tell you that the proper codecs are not installed, and it will then prompt you to install them. Just hit ok and BINGO the codecs are installed, without using a 3rd party app.

---

### Post by Blue Ocean on 2007-06-11
> **ruialexbarbosa said:**
> I'm sorry but I have to be honest on this one:

You are pissed off with XP so you move to Ubuntu, a free alternative (which I'm using 99% of the time now, despite knowing next to nothing about Linux) and you want to give up because it's not a lot better than xp? If xp is so good, well, easy choice...


Yeah thanks. I'm glad it works for you - what I'm saying is that at right now, Ubuntu isn't doing anything for me. I know if I can get it to work I'd use it over XP - I'm not saying it's 'not a lot better than XP', I'm saying I can't do anything useful with it at the moment.
-------------------------------------------------------------
I keep getting errors when I try to install ndiswrapper using *sudo make install* - I've saved the output as a text file but it's very long so I'm not sure if I should post it.

---

### Post by dptxp on 2007-06-11
Suggest retain Ubuntu. Use when possible and get familiar. Sort out your problems with the help of the forums. It can take time but then you shall have true FREE OS.
It occupies some space on hard disk. That is all you invest in.

---

### Post by jcronkhite on 2007-06-11
I had similar frustrations when I began using Ubuntu with my old hardware.  Fortunately, I found myself in a position to upgrade and bought a new laptop.  I was sure to choose hardware I knew would be Linux friendly (most hardware is), avoiding things like ATI and Broadcomm Wireless (although I got the Broadcomm working on my old laptop, I didn't like the speed).

I'm not saying that if you fail to get Ubuntu working quickly on your existing system to buy a new one.  That's really against what Linux is all about.  I spent a lot of time combing the forums here and was finally able to get Ubuntu working on my old laptop (even though it's been replaced since).  Please don't give up!  You can do it!

If time is of essence, maybe you can come back to Ubuntu later when you have the time to spend on your hardware.  Or, you can purchase a compatible wireless card and perhaps solve the problem that way.  Personally, I'd rather waste my money on a wireless card and reap the benefits of all of the great free software OpenSource in general has to offer then go back to Windows for everyday things.

In any case, let us know if you don't mind what you choose to do.

---

### Post by Wim Sturkenboom on 2007-06-11
> **Wim Sturkenboom said:**
> And you can align your screen position in that config file as well. I will try to come back on that as well

Use a modeline calculator and add the result to the screen section. Examples:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://zaph.com/Modeline/](http://zaph.com/Modeline/)

For the former fill in horizontal and vertical size (1280, 1024) and vertical refresh (75) in the basic configuration, and you will get a result like
```
Modeline "1280x1024@75" 156.43 1280 [COLOR="Red"]1312 1904[/COLOR] 1936 1024 1043 1056 1076
```

The latter works similar, but the output format is slightly different. You can quite easily convert it to above format.

According to [http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/fixes.html#AEN437](http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/fixes.html#AEN437) , you should play with the red numbers to move the picture.

Please note:
I've only done this once (long ago) and did it differently (trial and error) so can not be more accurate.


Two last remarks:
1)
My Matrox G400 video card (late nineties) came with software for Windows that allowed me to adjust these settings as well (Win98). So if it can be done in windows, it might be a lot easier; set it correct for Ubuntu with the monitor controls and next adjust the settings using the utility under windows
2)
You might be able to get the numbers from the windows inf file that came with your monitor (unfortunately I don't have the floppy for my monitor at hand so I can't check).

---

### Post by ezsurfer on 2007-06-11
When I first installed mine on my previously windows based system, I never got any feedback for setting up the router access code (Passwords).  Once I did this, then everything was fine.  Have you set up the LAN admin on the Ubuntu PC?

---

### Post by phr0ze on 2007-06-11
The reason the screen is off the monitor is because the frequency is not the same as it is in windows. If you match them up it'll be fine. Someone on page one posted how to modify your xorg.conf file.

---

### Post by ugm6hr on 2007-06-11
> **Blue Ocean said:**
> I keep getting errors when I try to install ndiswrapper using *sudo make install* - I've saved the output as a text file but it's very long so I'm not sure if I should post it.

Might be worth trying ndiswrapper (slightly older version 1.38) in the Fiesty repo.  Obviously, if you're not online already - you will have to download bits manually (assuming you are using Feisty):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_1.38-1ubuntu1_all.deb&md5sum=4174f813139217e8e814562eed795977&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_1.38-1ubuntu1_all.deb&md5sum=4174f813139217e8e814562eed795977&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)

Then just double click on all these in order to install.
Windows wireless driver tool should appear in the System Menu, allowing you to pick your .inf file.
I think some modprobe editing is required - and it's been a while since I did this, so I can't remember how it's done.

The only other problem is which Windows driver to use.  Have a look at the appropriate entry for your card on (there are 2 versions listed of your card):
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

---

### Post by Blue Ocean on 2007-06-11
Thanks very much - I will try some of this stuff out soon when I get some time - bear with me seeing as I have to keep booting back and forth to be able to read your posts!

---

### Post by Blue Ocean on 2007-06-12
> **ugm6hr said:**
> Might be worth trying ndiswrapper (slightly older version 1.38) in the Fiesty repo.  Obviously, if you're not online already - you will have to download bits manually (assuming you are using Feisty):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_1.38-1ubuntu1_all.deb&md5sum=4174f813139217e8e814562eed795977&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndiswrapper%2Fndiswrapper-source_1.38-1ubuntu1_all.deb&md5sum=4174f813139217e8e814562eed795977&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu3_all.deb&md5sum=428a69f0cfa33b978a6ae325772f1aae&arch=all&type=main)

Then just double click on all these in order to install.



I can install the 'common' file, but the other 2, gtk and the ndiswrapper source say they need something else. Gtk says it needs ndiswrapper-util 1.9 and the source package says it needs module-assistant.

---

### Post by 67GTA on 2007-06-12
You might want to try Linux Mint. It is basically Ubuntu with all of the stuff you have to hunt down and install for daily use already installed.

---

### Post by Brightbelt on 2007-06-12
Hi Blue Ocean,
I may have arrived too late but,....something is confusing me. You said you can't get your linksys adaptor to accept WPA protection and so it sounds like you're saying that the adaptor is limited and is incompatible with WPA.

But then later you say that it works fine in XP with WPA. Are you referring to the same linksys adaptor? If you are, then you should be able to get WPA to work with it in Ubuntu. The WPA Supplicant is supposed to be installed by default in Ubuntu Feisty. 

But just in case, if you're  in Ubuntu Feisty, you can run this: 

sudo apt-get install wpasupplicant 

Also, can refer to this page if you need assistance:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29) 

It's something to try anyway.  Linux can take some time. If you've got a dual boot like I have, why not keep it a while and see? 

I hope this helped,...Frank B.

---

### Post by Blue Ocean on 2007-06-12
I mean in the network configuration utility in the top right corner, when I try to connect to my network, I only see options to enter WEP keys and no 'WPA Personal' option which I have seen in various screen-shots and I know some others have a similar problem. 

WPA supplicant is installed - that was one of the first things I tried after reading some guides. It says the latest version is already installed. I'm fairly confident its a driver issue - but I can't get ndiswrapper to work.

I'll try to keep it for a while - if I still don't get anywhere after a while then I'll say bye bye.

---

### Post by ugm6hr on 2007-06-12
> **Blue Ocean said:**
> I mean in the network configuration utility in the top right corner, when I try to connect to my network, I only see options to enter WEP keys and no 'WPA Personal' option which I have seen in various screen-shots and I know some others have a similar problem. 

WPA supplicant is installed - that was one of the first things I tried after reading some guides. It says the latest version is already installed. I'm fairly confident its a driver issue - but I can't get ndiswrapper to work.

I'll try to keep it for a while - if I still don't get anywhere after a while then I'll say bye bye.

Brightbelt makes a good point.  Have you successfully connected with an open / WEP network?  I realise that that would not be a final solution for you, but it would at least confirm that the drivers are working.  Might be worth *temporarily* opening your network security to have a try.  Getting WPA to work is generally not that hard, although some Linux drivers are not WPA compliant (I believe).

Also - because of the multiple issues you raised - the advice has been a bit hit and miss.

If you want to get wireless working - post the results of the following (in Terminal):
```
lsusb
```
```
ifconfig
```
```
iwconfig
```
You might find that gives us a clue.  Of course, if you've already started a separate thread with these details - point us back to it.

If you are sure you need ndiswrapper:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main)
This is ndiswrapper-util for i386 Ubuntu (i.e. 32-bit PC) - if you have an AMD64 installation - it's not too far away.  If you install this and gtk - it should work.  Sorry - you don't need source (that was a mis-click on my part).

As for your Linksys card (WUSB54G) - ndiswrapper wiki seems to suggest it works fine with v1 and v4  - there seems to be at least 3 different versions with different chipsets.  So the *lsusb* should hopefully identify exactly which one you have.

I hope that you can get this issue resolved.

---

### Post by arvevans on 2007-06-12
Hang in there and keep "playing" with Linux, but in the interim keep your Ms-XP and dual boot.  That way you have the advantage of something that you already know and use, while at the same time have Linux available to learn as your spare time allows.

Make sure that your Linux install includes mounting of the Windows file system.  This allows you a way to use existing network security via Ms-XP to download stuff for Linux and then reboot into Linux and copy that downloaded data from the Ms-XP file system.

There are several security systems for use with WiFi Hub/Routers.  Each has it's own strong and weak points, and each has been proven to be breakable by dedicated and knowledgeable individuals.  The best protection you have in either Linux or Ms-XP is a strong firewall (on Ms-XP you will also need an anti-virus program).  If you have control of your Hub/Router you can select the encryption level that works best for you.

I switched from Ms-based operating systems to 100% Linux about 3 years ago and now have no installed Microsoft products here.  Taken gradually, the learning curve for doing this is not all that bad (it's actually fun if you are not under production deadlines to make it work).  I still have some issues with Linux (older video camera will not work, oddball hardware may not work properly, etc.) but overall, it does the job and does it well.

_._

---

### Post by Blue Ocean on 2007-06-13
neel@neel-desktop:~$ lsusb
Bus 003 Device 005: ID 08ec:0008 M-Systems Flash Disk Pioneers 
Bus 003 Device 003: ID 13b1:000d Linksys 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

------------------------------------------------------------------------------------------

neel@neel-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:8C:18:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

rausb1    Link encap:Ethernet  HWaddr 00:12:17:96:AA:9D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19731 (19.2 KiB)  TX bytes:21840 (21.3 KiB)

------------------------------------------------------------------------------------------

neel@neel-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:""  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--------------------------------------------------------------------------------------------
Btw, I got ndiswrapper working and installed a driver from the CD that came with the adapter, but I don't think it made much of a difference. I haven't yet tried connecting using WEP or opening up the network. If you still think I need to try after looking at this, let me know.

I also managed to edit my xorg.conf file to get my refresh rate to 60Hz which is great. :D I haven't tried shifting my screen but I will have a go at that soon.

Thanks for your patience.

---

### Post by NfF on 2007-06-13
thx for the automatix software..im gonna try it and hey...can someone give detailed instructions to install the WUSB54G? like the dell website for example...i tried

---

### Post by ugm6hr on 2007-06-13
```
*Driver 0: Ralink driver: http://www.ralinktech.com/supp-1.htm - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid “usb X-Y: reset high speed USB device using ehci_hcd and address Z”) and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). ‘mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf’ should do the trick.*
```

From ndisrapper wiki.  Unfortunately, you have v4 of the USB wifi card - which is more problematic to get working.

Possible solutions (I have no idea whether they will work):
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
or
ndiswrapper + [http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
(try the XP driver)

Look for USB RT2500 for the correct driver to install.

---

### Post by beans on 2007-06-14
> **cwmoser said:**
> My suggestion is to perservere.  I have finally ridded myself of Windows on my home PC and I have found Ubuntu to be much faster and a better environment.  There is a learning curve but after a point it doesn't seem as much a struggle.

I'm running Ubuntu with QuickBooks, Quicken via CrossOver.  I've gotten VPN working, NXServer for remote access, ntfs-3g to access my windows paritions, been able clone my Linux partition, installed MonoDevelop and compiled some C++ programs using GTK++, and installed numerous apps.  It has been a rewarding learning experience and should enhance my resume.

Carl

When i got my new notebook with Vista I wiped it all out and decided to go 100% with Ubuntu... i still had another desktop where i could use quicken until i figured it all out... to no avail.
there seems to be nothing nearly as good as quicken OR ms money for a user that doesn't want to manually enter his transactions... i have a few accounts and a wife and older kids... so i have a LOT of transactions to keep up with...
so i wound up dual bootiing XP and Ubuntu on my notebook after a month or so.  and NOW find myself not bothering to boot into ubuntu since i tend to want to get into quicken quite often... oh, and roboform is a wonder of the ages too... these two apps, quicken (or msmoney), and roboform may well be the reason(s) i will not abandon windows, no matter how much i'd like to.

here's my rant.
which raises my question, why (oh why) are there SO many distros of linux, when the work needs to be done on the APPS?  gnucash, kmymoney whatever.

OSes are pretty much OSes now... i can do without beryl, but i cannot do without my checkbook... 20 plus years ago there were two things (we joked) that people did when they got a PC, balance their checkbook, and keep recipes... the checkbook part was no joke though.

this COULD be the killer app, one way or another, for linux.  ubuntu's default install is great for 90 percent of people SAVE for the lack on online banking software. skip a version of ubuntu,  leave off some bells and whistles and make an/one of the OSS checkbook apps work with online banking.

---

### Post by Bruce S on 2007-06-15
Greetings Beans,
 I have just installed Ubuntu 7.04, and have used Firefox to get onto my two banking accounts.
 Have no problems at all. 
  I am definitly not a Geeg, and have not got a clue about programming.
  What one fool can do , another surely can. ( To quote an auther in book on Calculus)

---

### Post by samuraiCat on 2007-06-15
> **Bruce S said:**
> Greetings Beans,
 I have just installed Ubuntu 7.04, and have used Firefox to get onto my two banking accounts.
 Have no problems at all. 
  I am definitly not a Geeg, and have not got a clue about programming.
  What one fool can do , another surely can. ( To quote an auther in book on Calculus)

Bruce and beans:

I think what beans is lamenting here is that software like TurboTax and Quicken have no equivalents in Linux yet--which may or may not be true, since it is a bit tough to discern the purpose of a Linux program from its name (what the hell does the word "Hydrogen" have to do with the act creating audio loops, for example).

---

