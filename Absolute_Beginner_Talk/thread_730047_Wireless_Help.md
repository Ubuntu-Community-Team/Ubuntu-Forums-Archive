---
title: "Wireless Help"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2008-03-20
Okay, so When i was running windows on my computer i was able too have wireless internet on it. it is a desktop computer, but i had it downstairs in my basement. after i installed linux onto my computer, i cannot figure out how too get the wireless internet working again. i have too plug the computer in directly too the wireless router, if anyone could help me get my wireless internet running again, that would be great.
=]

---

### Post by 00arthuryu on 2008-03-20
if you have the wireless drivers for it, then ndiswrapper should do the trick
the hard part is to find the wireless drivers though, on mine i tried 3 of them and only 1 would work

regards
arthy

---

### Post by scuba_steve_va on 2008-03-20
Well...get ready to start on a long journey.  :-|


Wireless support in Linux is nowhere near as straightforward as it is in Windows.  Nothing is plug and play.  Getting anything working typically requires running Windows drivers inside a Linux wrapper utility.  There are many threads on the topic...and many frustrated posts by people who cannot get it to work.

If you can stay wired, do it.  If you cannot, I suggest using a wireless bridge.  Of course, you can also search here and find some fairly detailed posts by helpful folks who have gotten their setup working...but your mileage may vary when you attempt to apply these solutions.  Mine sure did.  Me?  I am using a bridge...and not letting Ubuntu know that it is on a wireless network.

---

### Post by tad1073 on 2008-03-20
We need to know a little about your system.

Open a terminal and post the output of:
```
lspci
```
```
lshw -C network
```

---

### Post by dylondadank on 2008-03-20
dylan@chaos:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem



dylan@chaos:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:17:31:b0:8d:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by TeoBigusGeekus on 2008-03-20
Why don't you try WICD?
[http://ubuntuforums.org/showthread.php?t=705391]("http://ubuntuforums.org/showthread.php?t=705391")

---

### Post by tad1073 on 2008-03-20
try wicd first, then if that doesn't work, I will try to help the best I can.
[Supprted wireless cards](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by dylondadank on 2008-03-20
> **tad1073 said:**
> try wicd first, then if that doesn't work, I will try to help the best I can.
[Supprted wireless cards](http://ubuntuforums.org/showthread.php?t=370108)

when trying to install wicd an error reads

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-i386_Packages)
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by TeoBigusGeekus on 2008-03-20
Never mind the errors, can you add the line
```
deb http://apt.wicd.net gutsy extras
```
in your third party software repositories?

---

### Post by dylondadank on 2008-03-20
yeah, in the third party repositories.. if it did instal, where would i find the file? it is not on the desktop

---

### Post by TeoBigusGeekus on 2008-03-20
Click reload and search for wicd.
When you find it, right click it and select install.
Then go to applications->internet->wicd.

---

### Post by dylondadank on 2008-03-20
okay, now it is installed, i opened it. and now the internet does not work on my computer, i am now using my windows computer upstairs! ahhhh

---

### Post by TeoBigusGeekus on 2008-03-20
What did you do when you launched the application?

---

### Post by dylondadank on 2008-03-20
i just launched it, and the internet stopped working. 

what i need to happen is get the internet working with either the "Netgear WG111T 108 Mbps Wireless USB"

or the "Netgear WG111 54Mbps Wireless USB "

preferably the WG111T because where the computer will be located is 2 floors below where my wireless router is. but now i can not even be on my linux computer =[ no internet

---

### Post by tad1073 on 2008-03-20
[Have a look at this thread](http://ubuntuforums.org/showthread.php?t=538448&highlight=realtek), [and this one also](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by dylondadank on 2008-03-20
> **tad1073 said:**
> [Have a look at this thread](http://ubuntuforums.org/showthread.php?t=538448&highlight=realtek), [and this one also](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

The first threads help did not work, and the second thread, well i dont really know what to use that for, im noobish with ubuntu =[ got most of the basics! dang this is stressfull!

---

### Post by dylondadank on 2008-03-20
any help? 
i am left with no internet connection at all now

---

### Post by imdano on 2008-03-20
What's happening when you try to connect with wicd?  Did you check the preferences to make sure your wireless interface was detected correctly?  Is wired not working either?

---

### Post by dylondadank on 2008-03-20
> **imdano said:**
> What's happening when you try to connect with wicd?  Did you check the preferences to make sure your wireless interface was detected correctly?  Is wired not working either?

I restarted my comoputer, too see if it would connect then, no connection still, and when i try too run wicd, it wont even start up anymore. i havent checked any preferences, i dont know what too do there, and no, wired is not working either, it has been wired for awhile, and working. but i need it too switch back too wireless, it has never worked wireless with ubuntu, only windows. thats what i need help with. but now i just need to get my connection too the internet back

---

### Post by imdano on 2008-03-20
Ok, to try and fix wicd, first try running "sudo /etc/init.d/wicd start" in the console, then try opening the wicd tray with ```
/opt/wicd/tray.py
```If that doesn't work, try opening up /opt/wicd/data, and deleting all the files in there that end with .conf, then repeat the above steps.  It should open correctly then.

Also, you can probably connect manually through ethernet at the command line using ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by dylondadank on 2008-03-20
okay, so i am stupid. i got my internet working back on my computer with linux, simply by going into network settings and doing wired connection. so that is a plus. now i just need help getting the wireless internet too work with the "Netgear WG111T 108 Mbps Wireless USB"

---

### Post by tad1073 on 2008-03-20
try system>admin.>network>wireless>properties>enable roaming
and see if that works.

also, try right-click on network icon>connect to another network, type in your network essid> then select if it is wep, wpa or wpa2, enter pass phrase

---

### Post by dylondadank on 2008-03-20
the only problem is-
in the system>network> there is only "wired connection" & "modem connection" too choose from

---

### Post by tad1073 on 2008-03-20
have you enabled restricted dirvers manager?

---

### Post by dylondadank on 2008-03-20
the only component in the restricted drivers is my graphics card

---

### Post by tad1073 on 2008-03-20
go through [these posts](http://ubuntuforums.org/search.php?searchid=38120696) to see if you can find a solution. I have done all i know to do.

Have you tried to install ndiswrapper?

---

### Post by dylondadank on 2008-03-20
i have installed ndiswrapper, just about an hour ago. i dont know where it is located though, and once opened i most likely will not know what too do with it

---

### Post by TeoBigusGeekus on 2008-03-20
Have you tried to reboot in order to see if you can get something else than wired and modem connection?

---

### Post by dylondadank on 2008-03-20
> **TeoBigusGeekus said:**
> Have you tried to reboot in order to see if you can get something else than wired and modem connection?

yeah, i have rebooted twice =[

---

### Post by TeoBigusGeekus on 2008-03-20
So, to sum up, you got wicd working with a wired connection but going to system->administration->network tools
you don't see a wireless connection.

---

### Post by dylondadank on 2008-03-20
i dont even know if wicd is working now, it wont open anymore.

but in system>admin>network there is no wireless. just wired and modem.

---

### Post by imdano on 2008-03-20
I posted instructions for getting wicd to work again upthread.  Whats the output of ```
iwconfig
iwlist scan
lsusb
```

---

### Post by TeoBigusGeekus on 2008-03-20
Open a terminal and type
```
/opt/wicd/gui.py
```
and see what messages you get.

---

### Post by dylondadank on 2008-03-20
> **imdano said:**
> I posted instructions for getting wicd to work again upthread.  Whats the output of ```
iwconfig
iwlist scan
lsusb
```

dylan@chaos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dylan@chaos:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


dylan@chaos:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000

---

### Post by dylondadank on 2008-03-20
> **TeoBigusGeekus said:**
> Open a terminal and type
```
/opt/wicd/gui.py
```
and see what messages you get.

dylan@chaos:~$ /opt/wicd/gui.py
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined

---

### Post by imdano on 2008-03-20
I think he's going to get a DBUS error saying that org.wicd.daemon doesn't exist.

edit: like the one he posted.

Look at my post about getting wicd to work upthread, dylon.

double edit: That output you posted doesn't show your usb network card at all.  Are you sure it works?

---

### Post by TeoBigusGeekus on 2008-03-20
Look carefully at this page
[http://wicd.sourceforge.net/wiki/doku.php?id=faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq")

---

### Post by dylondadank on 2008-03-20
> **TeoBigusGeekus said:**
> Look carefully at this page
[http://wicd.sourceforge.net/wiki/doku.php?id=faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq")

i reinstalled, still the program will not come up. the link too it in applictaions>internet is there, but it wont run. it ran earlier today, now it will not

---

### Post by TeoBigusGeekus on 2008-03-20
Then the only thing I can suggest is to go to synaptic, mark wicd for _complete_ removal and reinstall gnome network manager or wicd again - if you feel you haven't explored its settings in their entirety.

---

### Post by imdano on 2008-03-20
Dylon, I am one of the developers of wicd.  Reinstalling will not help because your configuration files will remain after being uninstalled, so if there is something wrong with them the problems will remain.  Open up the /opt/wicd/data directory, and delete all the .conf files.  Then run ```
sudo /etc/init.d/wicd start
```I think you will be able to open up wicd then.

---

### Post by dylondadank on 2008-03-20
after a complete uninstillation, what would be your next recommendation?

---

### Post by tad1073 on 2008-03-21
find some drivers that work. Or get a new wifi card. this is my second one.

---

