---
title: "Wireless network card Atheros"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2008-01-27
Hello all,
Ubuntu shows the model of my wireless network card atheros ar5006 but in windows vista is the card atheros ar5007?!
Ubuntu doesn't know my wireless card. Could someone help me to install the correct driver for the wireless card?
Thanks,

---

### Post by overdrank on 2008-01-27
> **linux-beginner said:**
> Hello all,
Ubuntu shows the model of my wireless network card atheros ar5006 but in windows vista is the card atheros ar5007?!
Ubuntu doesn't know my wireless card. Could someone help me to install the correct driver for the wireless card?
Thanks,

HI  and my Acer laptop is the same and this thread helped me
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
Good luck!

---

### Post by sheki1 on 2008-01-30
Hi, I think i have the same problem as you...

I followed that Atheros thread but it wasn't helpful. At least for me... 

My problem is that I cannot connect to the wired network (with Ubuntu) because of the location of the router so I cannot d/l any of those drivers or apps or utils to get them working.

I've got a HP DV6768se (notebook) with the Atheros wireless card. 

I can connect to my wireless with Vista  and went to download wicd, but the d/l instructions assume you can CONNECT to the website. 

Any help would be greatly appreciated!!!

---

### Post by stchman on 2008-01-30
> **linux-beginner said:**
> Hello all,
Ubuntu shows the model of my wireless network card atheros ar5006 but in windows vista is the card atheros ar5007?!
Ubuntu doesn't know my wireless card. Could someone help me to install the correct driver for the wireless card?
Thanks,

I too have an Atheros ar5006 and it works very well using Feisty.  Does your wireless card work?

---

### Post by ugm6hr on 2008-01-30
> **sheki1 said:**
> I can connect to my wireless with Vista  and went to download wicd, but the d/l instructions assume you can CONNECT to the website. 


If you want to install Wicd - download the .deb (stable) from here:
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

Double-click the .deb, and it will install.

Then follow the website instructions to get the tray app working.

---

### Post by sheki1 on 2008-02-02
I d/led the file (with Vista) and copied to a dir that Ubuntu can see and then rebooted into ubuntu.

I double clikcked on the icon, but when it run it gives me an error msg, "conflicts with the installed package network manager."

any further help would be appreciated.    THANKS!

---

### Post by ugm6hr on 2008-02-02
> **sheki1 said:**
> I double clikcked on the icon, but when it run it gives me an error msg, "conflicts with the installed package network manager."

You have to uninstall *network-manager* in Synaptic Package Manager.  It should then allow you to install.

---

### Post by sheki1 on 2008-02-02
ok, I uninstalled the network-manager in Synaptic Package Manager... then I got a msg "the network manager applet could not find some of the required resources. It cannot continue."

then I d-clciked the .deb file and was able to click 'install package'.

then I got Installation finished, pack wicd_1.4.1-all,deb was installed. And shows a teminal icon which I clicked and got the following...

Selecting previously deselected package wicd.
(Reading database ... 87952 files and directories currently installed.)
Unpacking wicd (from /media/sda8/wicd_1.4.1-all.deb) ...
Setting up wicd (1.4.1) ...
Stopping wicd daemon...
 Removing any system startup links for /etc/init.d/wicd ...
 Adding system startup for /etc/init.d/wicd ...
   /etc/rc0.d/K20wicd -> ../init.d/wicd
   /etc/rc1.d/K20wicd -> ../init.d/wicd
   /etc/rc6.d/K20wicd -> ../init.d/wicd
   /etc/rc2.d/S80wicd -> ../init.d/wicd
   /etc/rc3.d/S80wicd -> ../init.d/wicd
   /etc/rc4.d/S80wicd -> ../init.d/wicd
   /etc/rc5.d/S80wicd -> ../init.d/wicd
Stopping any running daemons...
Starting wicd daemon...
/opt/wicd
wicd daemon: pid 13465


is this what's supposed to happen?   what do I do next?

---

### Post by ugm6hr on 2008-02-02
> **sheki1 said:**
> is this what's supposed to happen?   what do I do next?

Sounds like it installed OK.

Now follow the instructions on Wicd website to auto-launch the applet on startup (quoted below).
> In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".
Then reboot.

Then Wicd is installed.  Presumably you can now follow the other thread?

EDIT:
Just seen the other thread...  It uses ndiswrapper.  The wget commands will also require a working internet connection.  Assuming that advice works - you can still achieve the same outcome:
You need to download this ([http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)) from Vista
Are you running 64 bit Ubuntu or ordinary i386?  ndiswrapper packages are available for Gutsy, but which one you need is dependent on the architecture.  I'll let you know which ones to download if you don't understand the links below.
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)
Put all the files in /home/username
Double click on the -common and -utils-1.9 ndiswrapper packages (in that order)
tar xvf ar5007eg-*.tar.gz
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
Then continue from instruction 6 in How-To (I don't know some of the commands there though).

---

### Post by sheki1 on 2008-02-02
I've got 64 bit Ubuntu.

Don't know how to copy files to /home/username.

I've downloaded (with Vista) ar5007eg-64-0.2, madwifi-0.9.3.3, ndiswrapper-1.5 and have extracted them all tho their individual directories...

By the way, I noticed I had a typo before and now after I rebooted I se the wicd tray. When I click on it the Wicd Manager windows opens, but it says No wireless networks found. 

the WPA supplicant driver is wext, and I changed the woreless interface to wlan0 (just it showed on that website) and clicked ok and hit refresh, but nothing changed.

---

### Post by ugm6hr on 2008-02-02
My fault for starting half-way.  I was assuming you just wanted to install Wicd.  You have done that now - but it won't change anything if your wifi card is not supported.  So let's start from the beginning.

Post the output from:
```
lspci
lshw -C network
```

That will identify your wifi card.  We'll take things from there.

---

### Post by sheki1 on 2008-02-02
lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

 lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth7
       version: a3
       serial: 00:00:6c:bf:1a:2e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

btw, I did download (with Vista) drivers from other posts re: Atheros, but dunno what to do them with them... all the posts start with dget or sudo or something else that doesn't seem to give me any clue...

---

### Post by ugm6hr on 2008-02-03
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

I gather (from other posts) that this is a new Atheros chipset that is supported by madwifi, but only in the latest version (0.9.3.3).  I will do a quick search and get back to you.

If you want to have a look yourself:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)

---

### Post by ugm6hr on 2008-02-03
A bit of research shows that there may be a different problem here.

It appears Linux identifies the AR5007EG as 5006EG.  That is probably the problem.  Madwifi works, but only if you use a patched version.  This gives a summary which should work (apparently):
[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)
In combination with: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Someone else who's trying: [http://ubuntuforums.org/showthread.php?t=685692](http://ubuntuforums.org/showthread.php?t=685692)

Otherwise, ndiswrapper appears to work: [http://ubuntuforums.org/showthread.php?t=649019](http://ubuntuforums.org/showthread.php?t=649019)

---

### Post by sheki1 on 2008-02-03
hi, I didn't want to have to switch to too many diff threads so I'll stick with this one if that's ok?

I followed [http://ubuntuforums.org/showthread.php?t=685692](http://ubuntuforums.org/showthread.php?t=685692)

but found some problems... I disabled the HAL driver, rebooted and went to the synaptic program

I was able to select the 2nd & 3rd options, but not the first (ndisgtk).  it asked me for the CD and I put it in and was able to install the ndis... options.

I got the atheros driver and unpacked it, but when I look for go...
to system-administration-Windows Wireless Drivers, I cannot find it.

at this point I dunno how to install the inf drivers...

> install ndiswrapper from synaptic --- you can select the following packages:

ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9

after installing ndiswrapper get windows drivers files, I personaly went to [http://www.atheros.cz/](http://www.atheros.cz/)
and select the correct one (in my case was ar5006eg)

extract the file (in my case was xp32-5.3.0.56-whql.zip)

goto goto system-administration-Windows Wireless Drivers


click on Install New Driver

click on location then browse to where you extracted your windows file

Select the file with extension .inf

click on Open then click on Install

you can close Windows Wireless Drivers after you see a confirmation that hardware is present.

---

### Post by ugm6hr on 2008-02-03
> **sheki1 said:**
> I got the atheros driver and unpacked it, but when I look for go...
to system-administration-Windows Wireless Drivers, I cannot find it.

at this point I dunno how to install the inf drivers...

Where did you download the atheros driver?  Where did you unpack it?

Firefox defaults to Desktop - so try looking there.  If not - download the driver to /home/*username*, then extract it (by double-clicking).  You should then be able to find the .inf in the /home/*username*/xp-32-5.3.... folder.

---

### Post by sheki1 on 2008-02-04
hi, I got the driver from  [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
and I unpacked it to it's own sub-directory...

when I stated "to system-administration-Windows Wireless Drivers, I cannot find it.", I meant I could not find the "Windows Wireless Drivers" on the system-administration menu.

I also couldn't find "ndisgtk" on the synaptic manager...

---

### Post by ugm6hr on 2008-02-04
> **sheki1 said:**
> hi, I got the driver from  [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
and I unpacked it to it's own sub-directory...

when I stated "to system-administration-Windows Wireless Drivers, I cannot find it.", I meant I could not find the "Windows Wireless Drivers" on the system-administration menu.

I also couldn't find "ndisgtk" on the synaptic manager...

Sorry.  Misunderstood.  Also - can you repost which thread you are following, with *precise* details of what you have done, and where it fails.  It feels like I'm leading you blindly.

Anyway...

ndisgtk won't appear in Synaptic unless you have already got a working internet connection.  "Windows Wireless Drivers" is the menu entry for ndisgtk - hence it won't appear until ndisgtk is installed.

To get around this - download this:
[http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_amd64.deb)
This is the **64-bit** (AMD64) package.  If you are not on 64-bit - please report back.
Just double-click the package, and it should install.  If it doesn't - it means you haven't (yet) installed the necessary components:
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_amd64.deb)
Download these and double-click (in this order), then try double-clicking the ndisgtk package again.

After all that - the "Windows Wireless Drivers" will appear somewhere in the menu.

---

### Post by sheki1 on 2008-02-04
I was following the post you suggested at I followed: [http://ubuntuforums.org/showthread.php?t=685692](http://ubuntuforums.org/showthread.php?t=685692)

or I thought I did... I've opened so many dif threads my head hasn't stopped spinning...

but it did say to "install ndiswrapper from synaptic --- you can select the following packages:

ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9

after installing ndiswrapper get windows drivers files, I personaly went to [http://www.atheros.cz/](http://www.atheros.cz/)
and select the correct one (in my case was ar5006eg)

extract the file (in my case was xp32-5.3.0.56-whql.zip)"

I will try those new files when I get home tonight as I can't copy from work computer to personal...

---

### Post by ugm6hr on 2008-02-04
> **sheki1 said:**
> I was following the post you suggested at I followed: [http://ubuntuforums.org/showthread.php?t=685692](http://ubuntuforums.org/showthread.php?t=685692)


No you aren't.  That post is a user who is trying to get the patched madwifi drivers working.  And apparently unsucccessfully.

You are clearly trying to use ndiswrapper with the Windows drivers.

---

### Post by rbarra on 2008-02-06
Hi all,

I have the same problem: can't go wireless in my Acer Aspire 4720, using an Atheros AR5006X. I'm kind of desperate, because I have been trying many different tutorials and howtos.

I live in Chile and am a totally beginner in Ubuntu, but I want to learn.

If someone could guide me I would really appreciate it?

BTW: what is Wicd?

---

### Post by ugm6hr on 2008-02-07
> **rbarra said:**
> Hi all,

I have the same problem: can't go wireless in my Acer Aspire 4720, using an Atheros AR5006X. I'm kind of desperate, because I have been trying many different tutorials and howtos.

I live in Chile and am a totally beginner in Ubuntu, but I want to learn.

If someone could guide me I would really appreciate it?

BTW: what is Wicd?

I would recommend you start a new thread, since the OP has not been solved, and it gets confusing if 2 people are being helped.

Don't forget to include the following information in your post:
```
lspci
lshw -C network
```

Also - point us towards the How-Tos you have used.

For Wicd - follow the link below.

---

