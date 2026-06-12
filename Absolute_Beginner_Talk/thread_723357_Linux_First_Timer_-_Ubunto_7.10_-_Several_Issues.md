---
title: "Linux First Timer - Ubunto 7.10 - Several Issues"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Mike C on 2008-03-13
I posted some of these issues in the Installations forum but maybe I need to start here and get the info as an absolute beginner.  I have no Linux or Unix experience.  I've used Windows most of my life.  As far as Linux goes, I am an absolute beginner.

I want to give Linux a try for various reasons.  I recently installed Ubuntu 7.10 on an Acer Travelmate 2300, 1.5 GHZ Celeron and 512 MB ram.  It was running XP but I erased everything and did a new install.  Ubuntu is the only OS on the laptop now.

There are two main problems that I am trying to address right now.

- Wireless does not work.  I get Internet when I plug into a cable.  But my router is in an inconvenient corner of my basement.  I pretty much run a wireless network.  So without wireless this laptop is not online.  I've been doing my troubleshooting by downloading files to another computer and then transfer them to the Ubuntu machine.

- I can not get anything more than a basic graphics setup.  I know my graphics card is capable of much better graphics than what I am able to get right now.

- I also will need to address printing.  But I know that printing to my Lexmark laser printer through my wireless network will be difficult to accomplish in Linux.  I haven't started to play with this yet.


The wireless is my main focus right now.  I believe troubleshooting the other issues will be much easier once this machine has an active Internet connection.

So... here is where I stand with my issues at this point.


1)  In trying to get my wireless to work one of the first things I did was go through the Ubuntu wireless troubleshooting document.  The first step is, Check for device recognition: Open Device Manager (System &#8594; Administration &#8594; Device Manager). I try to do that but I do not see Device Manager listed on my menu. Is there some reason why I would not have Device Manager? Is this an indication that I had a problem during installation? Do I need to do something to manually install Device Manager?

2)  I tried initially to set up a Windows driver using the Windows Wireless Driver gui.  Whatever I did din't work and now the Windows Wireless Driver gui no longer opens.  When I click on Windows Wireless Drivers the password window comes up, I type in my password, then the Windows Wireless Drivers window starts to open but then immediately closes. I am unable to get it to stay open at all.  I know you can accomplish the same tasks through the command line but it would be nice to get this to work again.  After my install I initially did not have the Windows Wireless Driver gui.  I had to manually install ndisgtk and that worked.  I tried to reinstall that package now and I still have the same problem with the gui.

3) The driver that I installed is the driver for the INP2220, which is correct for my card.  Following someone's instructions I typed "sudo ndiswrapper -i neti2220.inf" to manually install and I got a message stating that driver was already installed.

4) Regarding my video, I tried a couple times to manually set my display settings and ended up messing up my display to the point where it wasn't readable.  It took me a while to figure out how to get it back to normal.  I read a few places stating that Envy works so I tried to install that.  When I try to install Envy I get a message stating "Dependency is not satisfiable: debhelper".  So I try installing debhelper and I get a message saying "Dependency is not satisfiable: dpkg-dev" But dpkg-dev is already installed.  Not sure where else to go with this.


I know this is a long post but I am stuck and I just don't know where else to go with this.  I feel like I'm getting close but at this point I am clueless as to what I should do next.

Thanks in advance for your help!

---

### Post by dca on 2008-03-13
did you type 'sudo modprobe -i ndiswrapper' at command line to insert wireless into the running kernel?

---

### Post by Mike C on 2008-03-13
> **dca said:**
> did you type 'sudo modprobe -i ndiswrapper' at command line to insert wireless into the running kernel?

I hadn't done that before.  I just tried it and rebooted and it doesn't seem to have made a difference.

---

### Post by dca on 2008-03-13
When using 'ndiswrapper', after installing the driver using the 'ndiswrapper' command you have to insert it into the kernel.  After running the command I told you, you should be able to click on the network monitor on the top right panel and see wireless access points.  If you can't then possibly the wrong driver is being used or a step in the instructions (possibly the blacklisting of the not needed driver) has been missed...

---

### Post by forrestcupp on 2008-03-13
I have never heard of something called Device Manager in Linux.

For your wireless, the first thing to check is go to System->Administration->Restricted Drivers Manager and see if there happens to be a restricted driver already listed for your wireless card.  If so, enable it, and it should just work, maybe after a restart.  If your wireless isn't listed there, then you'll have to go from there and do more work, probably with ndiswrapper.  But check the Restricted Drivers Manager first.

About your Lexmark printer.  You'll have headaches getting that worked out plugged in, let alone wirelessly.  Lexmark isn't known for being very Linux compatible.  I do have a Lexmark X5150 that I at least got printing working.  No luck on the scanner, though.

About Envy.  You need to open up Synaptic and go to Settings->Repositories.  In that screen and in the Ubuntu Software tab, make sure that all of the boxes are checked.  Then close that screen and hit the Reload button.  Then try installing the Envy deb again and it should work.

---

### Post by kesman on 2008-03-13
What version of ubuntu are you running? Device manager is actually in system -> preferences -> Hardware information in Ubuntu 7.10 Gutsy Gibbon. You should have this same version. I think you are trying to install a wrong version of Envy if it complains about dependencies.

Check that you have all sources ENABLED and cdrom DISABLED in sytem -> administration -> software sources to get the latest updates and other files.

EDIT: damn slow

---

### Post by Mike C on 2008-03-13
> **dca said:**
> When using 'ndiswrapper', after installing the driver using the 'ndiswrapper' command you have to insert it into the kernel.  After running the command I told you, you should be able to click on the network monitor on the top right panel and see wireless access points.  If you can't then possibly the wrong driver is being used or a step in the instructions (possibly the blacklisting of the not needed driver) has been missed...

I don't see wireless access in the network monitor.  I am pretty confident that I have the correct driver now.  But I may have installed an incorrect driver initially.  How do I know what drivers I have installed and what I need to blacklist?  Can you point me to some good instructions for doing the blacklist?

---

### Post by Mike C on 2008-03-13
> **forrestcupp said:**
> I have never heard of something called Device Manager in Linux.

For your wireless, the first thing to check is go to System->Administration->Restricted Drivers Manager and see if there happens to be a restricted driver already listed for your wireless card.  If so, enable it, and it should just work, maybe after a restart.  If your wireless isn't listed there, then you'll have to go from there and do more work, probably with ndiswrapper.  But check the Restricted Drivers Manager first.

About your Lexmark printer.  You'll have headaches getting that worked out plugged in, let alone wirelessly.  Lexmark isn't known for being very Linux compatible.  I do have a Lexmark X5150 that I at least got printing working.  No luck on the scanner, though.

About Envy.  You need to open up Synaptic and go to Settings->Repositories.  In that screen and in the Ubuntu Software tab, make sure that all of the boxes are checked.  Then close that screen and hit the Reload button.  Then try installing the Envy deb again and it should work.

- The only restricted driver I had was for my software modem.  Nothing for my wireless card.

- Is there a Linux dist that I should look into that would be better for wireless networking and printing to a Lexmark?

---

### Post by Mike C on 2008-03-13
> **kesman said:**
> What version of ubuntu are you running? Device manager is actually in system -> preferences -> Hardware information in Ubuntu 7.10 Gutsy Gibbon. You should have this same version. I think you are trying to install a wrong version of Envy if it complains about dependencies.

Check that you have all sources ENABLED and cdrom DISABLED in sytem -> administration -> software sources to get the latest updates and other files.

EDIT: damn slow

I installed what I thought was the latest release of 7.10.  Is Gutsy Gibbon 7.10?  Or does that refer to a specific release of 7.10?  How do I check what version/release I have installed?

---

### Post by forrestcupp on 2008-03-13
> **Mike C said:**
> 
- Is there a Linux dist that I should look into that would be better for wireless networking and printing to a Lexmark?

No.  Linux is Linux.  Distros are just Linux and the GNU OS packaged differently.  Lexmark just has crappy Linux support.  If you get your Lexmark and networking problems sorted out separately, you may find that Lexmark will work wirelessly.  I don't know.  I would think that the printer would have to be hooked up to some computer that all of the other networked computers can access.  I'm no expert on that, though.

---

### Post by Mike C on 2008-03-13
> **forrestcupp said:**
> I have never heard of something called Device Manager in Linux.

About Envy.  You need to open up Synaptic and go to Settings->Repositories.  In that screen and in the Ubuntu Software tab, make sure that all of the boxes are checked.  Then close that screen and hit the Reload button.  Then try installing the Envy deb again and it should work.

I just tried that but the reload won't work until I can get to a place where I can hook up to the Internet.

---

### Post by prshah on 2008-03-13
> **Mike C said:**
> I don't see wireless access in the network monitor.  I am pretty confident that I have the correct driver now.  But I may have installed an incorrect driver initially.  How do I know what drivers I have installed and what I need to blacklist?  Can you point me to some good instructions for doing the blacklist?

Alt+F2, type "gnome-control-center" look under the section "Hardware", click on "Hardware information".

What wireless card do you have? Either check in the above "Hardware information" or open a terminal (Applications-Accessories-Terminal) and post the output of the command ```
lspci | grep -i network
``` and ```
cat /proc/net/wireless
```

For a clue to your graphics problems, post/attach your /etc/X11/xorg.conf file.

Most network cards and wireless cards are now directly supported in Ubuntu 7.10, making the need for ndiswrapper and it's complexities unnecessary.

---

### Post by Mike C on 2008-03-13
> **prshah said:**
> Alt+F2, type "gnome-control-center" look under the section "Hardware", click on "Hardware information".

What wireless card do you have? Either check in the above "Hardware information" or open a terminal (Applications-Accessories-Terminal) and post the output of the command ```
lspci | grep -i network
``` and ```
cat /proc/net/wireless
```

For a clue to your graphics problems, post/attach your /etc/X11/xorg.conf file.

Most network cards and wireless cards are now directly supported in Ubuntu 7.10, making the need for ndiswrapper and it's complexities unnecessary.

For the command "lspci | grep -i network" nothing was returned.

For the command "cat /proc/net/wireless"  I got:
mike@mike-laptop:~$ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

My network card is:  [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

Here is my xorg.conf file:
------------------------------
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Mike C on 2008-03-13
> **forrestcupp said:**
> I have never heard of something called Device Manager in Linux.


You're the second person to tell me this.  But I swear I am taking this directly from their support docs for 7.10.

[https://help.ubuntu.com/7.10/internet/C/troubleshooting.html#troubleshooting-device](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html#troubleshooting-device)

--------------------
[I]Troubleshooting

This troubleshooting guide is designed to be carried out in order.

Check for device recognition

**1.  Open Device Manager (System &#8594; Administration &#8594; Device Manager).**

2.  Check to see the hardware is recognised if it is then the section called “Check for driver”

3.  If your device is not displayed then there ma be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.[/I]
--------------------

Is this a typo?  Are they refering to something else?

---

### Post by Astarroth on 2008-03-13
I don't know if this will help you are not but, I was having a simular problem with wireless and it seemed to start working after I deleted the ip6 hosts under the manual configuration of the network. Our local wireless network here at work just does not handle the ip6 protocals.

---

### Post by Mike C on 2008-03-13
Okay, I see now that the Device Manager is the name on the window when I launch Hardware Information from the Control Center.  That must be what they are referring to.

From the Hardware Information,

This is what it lists as my wireless card: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
This is what it lists as my graphics card: 82852/855GM Integrated Graphics Device

Those are both correct.

---

### Post by Mike C on 2008-03-13
> **Astarroth said:**
> I don't know if this will help you are not but, I was having a simular problem with wireless and it seemed to start working after I deleted the ip6 hosts under the manual configuration of the network. Our local wireless network here at work just does not handle the ip6 protocals.

How do I go about doing that?

---

### Post by Astarroth on 2008-03-13
Go to System, Administration, Networking. When the network settings opens up find and click on the Hosts tab. I deleted everything that started with ip6. It only left two entrys..
localhost and the one with my computers name.

---

### Post by emshains on 2008-03-13
I am sorry to hear that linux lets down new and hopfully trustful users.

For the lexmark printer try [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+wireless]("http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer+wireless")

The next ones are for wireless: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946")
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/]("http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/")

And maybe old threads will help:

[http://ubuntuforums.org/showthread.php?t=721724&highlight=Acer+Travelmate+2300+wireless]("http://ubuntuforums.org/showthread.php?t=721724&highlight=Acer+Travelmate+2300+wireless")

What kind of videocard do you have on the laptop? If its ATi it may be as well as unsolvable, because ati doesnt give much effort into making drivers for linux. It may be as well as a unconfigured driver, but thats kind of a best case scenario.

As a recent beginer, all i can say is: " Never give up, until you run out of coffee beans or battery life.  But dont put extremley high effort, if you have other things to do, if its not needed.

---

### Post by Mike C on 2008-03-13
> **Astarroth said:**
> Go to System, Administration, Networking. When the network settings opens up find and click on the Hosts tab. I deleted everything that started with ip6. It only left two entrys..
localhost and the one with my computers name.


Okay, I did that and it doesn't seem to have made a difference.

---

### Post by Mike C on 2008-03-13
I'm trying to follow the WiFiTroubleshooting doc.  [https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

Step 4 says to type iwconfig and that there should be at least one wireless extension available.  This is what I get when I type iwconfig:

lo  no wireless extensions.
eth0 no wireless extensions.

It doesn't say in the document what to do if there are no wireless extensions.

---

### Post by prshah on 2008-03-14
> **Mike C said:**
> For the command "lspci | grep -i network" nothing was returned.

My network card is:  [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

This card doesn't work with linux directly. So you will HAVE to use ndiswrapper for this.

> 

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection



Though your graphics device has been detected correctly, you are using the "generic" vesa driver. Either edit xorg.conf with the command ```
 sudo gedit /etc/X11/xorg.conf
``` and change the >  	Driver		"vesa" to > 	Driver		"intel" or reconfigure the entire conf file (I would suggest this) with ```
sudo dpkg-reconfigure xserver-xorg
```. If you use this to reconfigure, any time you have a doubt, go along with whatever it recommends.

After the entire process, restart your X by pressing Ctrl+Alt+Backspace. The screen should flicker a few times and then put you back on the login screen. If the screen remains blank or the monitor goes off, press Ctrl+Alt+F1, login as usual, then give the command ```
sudo cp -f /etc/X11/xorg.conf~ /etc/X11/xorg.conf
``` then switch back with Ctrl+Alt+F7, RELEASE all keys,  and then again press Ctrl+Alt+Backspace.

---

