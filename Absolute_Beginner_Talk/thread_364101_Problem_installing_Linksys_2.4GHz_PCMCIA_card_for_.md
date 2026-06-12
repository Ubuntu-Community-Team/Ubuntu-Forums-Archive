---
title: "Problem installing Linksys 2.4GHz PCMCIA card for Wi-Fi"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-17
I am new to Ubuntu and Linux. I have been looking through a lot of documentation to enable Wi-Fi. I have a Linksys 2.4GHz (54g) PCMCIA card. I would be ok with installing the software using command line, but I can't find instructions sufficient enough. Ideally, if there was a desktop utility to install software, that would be good too.

Thanks in advance for any help on this topic.

---

### Post by bmk789 on 2007-02-17
You should be able to enable your adapter and connect to a network using the Networking applet under System > Administration > Networking

If your wireless interface is not listed there you can try installing ndisgtk using Synaptic in System > Administration > Synaptic Package Manager

Ndisgtk will let you use a windows driver to run your wireless hardware in linux.

---

### Post by rbradshaw on 2007-02-18
Thanks for the reply, however, I did look in System > Administration > Networking, and found Icon entry for Wireless network where I defined my wireless network connection. Still, it does not work. I think the problem is that I don't have the drivers loaded for the card. I have not used Ndistgk... are you saying I should find my Windows driver from Linksys and use the Ndistgk utility instead of finding a Linux driver? I need specific details, please.

---

### Post by yemu on 2007-02-18
my wife is using linksys pcmcia card with windows drivers and it works pretty well.
you have to find your windows drivers and use them with ndisgtk. when you install ndisgtk you'll find "Wireless Drivers" or something similar (I don't remember as I'm not using it right now) in your System-Preferences menu. 
In your driver package there should be file with INF extenstion, that's the file you need.
Just start ndisgtk and install your card driver (point to the INF file when prompted).
also i suggest installing network-manager and network-manager-gnome (i don't remember the exact names - search for network manager in synaptic). it will give you a nice tray icon showing wireless networks (similar to the one found in Wi**ows).
i you have any question feel free to ask.
best regards
y

---

### Post by rbradshaw on 2007-02-19
thanks to everyone for your help. I am very close. I have installed ndisgtk, and now have a utility that let's me install windows drivers (.inf files). I downloaded some of the early versions of the driver, however, the utility said doesn't think there is hardware. I might have to keep trying other versions of the driver. How can I tell if the hardware is being recognized by the system unless I get the right driver? Unfortunately, when I download the zip file from linksys, it includes the autorun and windows software to installed a driver, when all I want is the driver itself.
 
Any thoughts on how to confirm which is the right version for my card?

---

### Post by Bachstelze on 2007-02-19
In a terminal, *ndiswrapper -l* will say "Driver installed, hardware present" when you have the correct driver. Then, all you need to do is *sudo depmod -a* and *sudo modprobe ndiswrapper* and voilà, your wireless interface will appear in *iwconfig*.

---

### Post by rbradshaw on 2007-02-19
I am on my 5th download of the various WPC54g drivers. After I download the zip file, I extract any of the INF files, and then I use the Windows Wireless Drivers tool under System Administration to install the driver. Every time (so far), the dialog box says hardware installed: no. It seems as if I am doing what was told to me, but still no luck. any thoughts?

---

### Post by Bachstelze on 2007-02-19
I can't help you with this, as I never use the GUI to do this. I just do *sudo ndiswrapper -i filename.inf* from a terminal and it always work perfectly. Does your car appear in *lspci* ?

---

### Post by rbradshaw on 2007-02-20
I ran lspci... here are results...

rbradshaw@rbradshaw-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420
02:01.1 CardBus bridge: Texas Instruments PCI1420
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

I don't think I have the syntax correct... please look at this and let me know.

rbradshaw@rbradshaw-laptop:~$ ls
carpet cleaning.odt  lsbcmnds.inf            Search Engine Keywords~
Desktop              ndiswrapper install     Technical Support.odt
Examples             Search Engine Keywords  Wireless Utilities
rbradshaw@rbradshaw-laptop:~$ sudo ndiswrapper -i lsbcmnds.inf[/i]
Password:
Installing i]
cp: cannot stat `lsbcmnds.inf[/i]': No such file or directory

---

### Post by rbradshaw on 2007-02-20
Sorry for the p.s....

what did you mean by [code]? does the /i terminate the command syntax or is it an option?

---

### Post by Bachstelze on 2007-02-20
sorry, that was a typo... Anyway, you got it right but your card doesn't apper here, what's the model name exactly ?

---

### Post by M0rThden on 2007-02-20
i seem to have the same problem. I followed all everything so far and my outcome is the same. only difference is that im using a different card

---

### Post by rbradshaw on 2007-02-20
If the card does not appear there, how can I find out why?

BTW - my card is Linksys WPC54g. Does this help?

---

### Post by rbradshaw on 2007-02-20
Sorry again for the p.s... I removed the card and inserted it into a different slot. I ran lspci again. Doesn't the end of the command show a wireless card?

03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Isn't this the card shown above?

---

### Post by Bachstelze on 2007-02-20
According to the Ndiswrapper Wiki, [this driver](ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe) will work with your card. It's an exe so use [i]cabextract[/i) to extract it.

---

### Post by M0rThden on 2007-02-20
my problem is that the programs says i installed the driver wrong. I have the WPC54GX4. and there is only one driver out. do you know what im doing wrong?

---

### Post by Bachstelze on 2007-02-20
Forget the goddamned GUI and use the terminal.

What does *ndiswrapper -l* say ?

---

### Post by rbradshaw on 2007-02-20
HymnToLife... thanks for the advice and your patience.

I am not familiar with the syntax before and after cabextract. can you explain please?

I looked on Wiki for cabextract instructions. I have desktop instructions, but where can I find instructions on the various Linux commands. I am looking for the equivalent of a Unix manual where I can read about any of the Unix commands including syntax. That would help me a lot.

---

### Post by Bachstelze on 2007-02-20
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

Here is everything you should need for a daily use. If you need something a bit more advanced, [http://www.linuxcommand.org/](http://www.linuxcommand.org/) is the place to go.

---

### Post by M0rThden on 2007-02-20
shatcher@shatcher-laptop:~$ ndiswrapper -l
No drivers installed
shatcher@shatcher-laptop:~$ ndiswrapper -i /home/shatcher/desktop/ tmimo3P.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
shatcher@shatcher-laptop:~$ ndiswrapper -l
No drivers installed


Thats how ive tried to install the drivers

---

### Post by M0rThden on 2007-02-20
ooppp... typo

shatcher@shatcher-laptop:~$ ndiswrapper -i /home/shatcher/desktop/tmimo3P.inf
Installing tmimo3p
Unable to create directory /etc/ndiswrapper/tmimo3p. Make sure you are running as root
shatcher@shatcher-laptop:~$


i think i see my problem...i think i need to log in as root and install it there

---

### Post by M0rThden on 2007-02-20
Ah well ill figure it out tommorow...off to bed for me

---

### Post by rbradshaw on 2007-02-20
HymnToLife.... 

I am going to forget this GUI... so much for making life easier. With the documentation you sent me, I am going to spend some time looking up ndiswrapper and cabextract before I post any more here. You have been patient - thank you.

From the ndiswrapper, I obviously have the wrong driver installed. Not sure how it happened, but it did. If you have any comments based on my latest output, let me know.

rbradshaw@rbradshaw-laptop:~$ ndiswrapper -l
Installed ndis drivers:
i]      invalid driver!
rbradshaw@rbradshaw-laptop:~$

---

### Post by rbradshaw on 2007-02-20
So, did some reading on cabextract, found the syntax and the other options. Downloaded a driver with .exe extension. Ran cabextract on file and received an error... what am I doing wrong?

cabextract 1.1 (C) 2000-2004 Stuart Caie <kyzer@4u.net>
This is free software with ABSOLUTELY NO WARRANTY.
rbradshaw@rbradshaw-laptop:~$ cabextract WMP54Gv4_20040415.exe
WMP54Gv4_20040415.exe: no valid cabinets found

All done, errors in processing 1 file(s)
rbradshaw@rbradshaw-laptop:~$

---

### Post by M0rThden on 2007-02-20
if you downloaded the correct drivers from the website extract the .ini file and the .sys file. i got mine to say this now:

shatcher@shatcher-laptop:~$ ndiswrapper -l
Installed ndis drivers:
tmimo3p driver present, hardware present 
shatcher@shatcher-laptop:~$ 


now ive done is and got this...any ideas?

shatcher@shatcher-laptop:~$ sudo depmod -a
shatcher@shatcher-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
shatcher@shatcher-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by rbradshaw on 2007-02-20
I would extract the files if I could... I ran cabextract on the .exe file and got an error. Any idea as to why?

---

### Post by M0rThden on 2007-02-20
I have no idea. Im new also. Im trying to figure out why sudo modprobe ndiswrapper gives me an error

---

### Post by butchd on 2007-02-21
Try downloading automatix2 (follow the install link).  It might make your hardware visible a lot easier (ndiswrapper to convert Windows drivers for network cards is included).

[http://www.getautomatix.com]("http://www.getautomatix.com")

---

### Post by chrish670 on 2007-02-24
> **yemu said:**
> my wife is using linksys pcmcia card with windows drivers and it works pretty well.
you have to find your windows drivers and use them with ndisgtk. when you install ndisgtk you'll find "Wireless Drivers" or something similar (I don't remember as I'm not using it right now) in your System-Preferences menu. 
In your driver package there should be file with INF extenstion, that's the file you need.
Just start ndisgtk and install your card driver (point to the INF file when prompted).
also i suggest installing network-manager and network-manager-gnome (i don't remember the exact names - search for network manager in synaptic). it will give you a nice tray icon showing wireless networks (similar to the one found in Wi**ows).
i you have any question feel free to ask.
best regards
y Hmmm.. I wonder if it makes a difference whether I use the win9x or winNT inf & drivers which came with my Linksys wi card.  I've copied the INF, SYS, and Cat files for win9X to a cd.

---

