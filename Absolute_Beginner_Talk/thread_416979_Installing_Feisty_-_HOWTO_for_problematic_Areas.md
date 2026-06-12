---
title: "Installing Feisty - HOWTO for problematic Areas"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by nickpaton on 2007-04-21
I've written this because so many people are asking questions on a range of topics from wireless, graphics cards, networking etc, and having now got a fully working system using topics posted elsewhere, I felt that this would assist others.

This is based on my HP nx6125 laptop however a lot of this will apply to other PC's.

I have supplied detailed descriptions on installing and setting up the following:

[B]Wireless with Broadcom 4138 chipset.
ATI Radeon Xpress 200M graphics card.
Setting up Peer to Peer network with XP PC.
Setting up firewall using Firestarter.
Printing via a printer attached to an XP PC.
Setting up the Synaptic Touchpad.[/B]

Install Feisty from a CD.  I used the 386 desktop 32bit version, even though my laptop is 64bit.

I simply followed the instructions given on the CD and had no problems.   Note that I had my wired LAN cable plugged in during the installation and the initial updates were done via wire.

I did note that my Broadcom 4138 chipset was not detected during installation.

I then installed various multimedia plugins, programs and apps I need, **EXCEPT** ndiswrapper and Network Manager

The following thread gives details of how to install multimedia plugins and restricted formats etc:

_[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")_

Easy Ubuntu or Automatix2 can also be used:

_[http://ubuntuforums.org/showthread.php?t=190535]("http://ubuntuforums.org/showthread.php?t=190535")_

_[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29")_

Please note that I will not enter into any discussion over whether Easy Ubuntu is better that Automatix or vice versa.  I have no views on the subject.


**_Broadcom 4318 Wireless Networking_**

This chipset seems to give a lot of problems.  However the following HOWTO has consistently worked for me in Dapper, Edgy and Feisty:

_[http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")_

Follow the simple set up for Feisty by downloading and installing the Feisty program.  
To install, go to the folder where you downloaded the program and double click on it.  In the new window click on the Install button and hit Close once it has installed.

Wireless was set up via System > Administration > Network and then setting up encryption settings as necessary &#8211; I use WEP.

Reboot the PC with the LAN cable removed and wireless should now work.

A Wireless Network Panel icon is available.
Hovering over the top panel, right click and select Add to Panel.
Select the Network Monitor icon within the System and Hardware section.
You will now have a wireless monitor with a bar indicator giving signal strength.


_**ATI Radeon Xpress 200M Graphics Card**_

Make a back up of your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

The graphics work fine out of the box, however I wanted to install the latest 3D drivers from ATI and tried various methods with no luck.
With this in mind, and thinking that I would have to reinstall the whole distro to clear the non working files, I tried the following HOWTO which not only worked but also tidied up all the old files as well:

_[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")_

Use Method 2.

If like me you tried other methods you will need to blacklist the old fglrx program as described.

**_DONT_** forget to carry out the instructions in the "Configure the Driver" section.

When I followed the aticonfig instructions, it actually deleted the contents of the xorg.conf file and it was only because I had made a backup of it that I could then restore it!
Instead, fire up xorg.conf file again ( *gksu gedit /etc/X11/xorg.conf * ), and in "Device" section replace the &#8220;ati&#8221; string with &#8220;fglrx&#8221;.

Reboot and test using glxgears from a terminal.

One thing to note is that every time a new kernel is issued, you will need to re-run the kernel compiler as described in the HOWTO.


_**Set up a Peer to Peer network with an XP PC**_

_[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")_

As it stands it states that the firewall needs to be disabled.

Instructions for setting up Firestarter so that the firewall can be enabled are in the next section.


**_Configure Firewall using Firestarter_**

_[http://ubuntuforums.org/showthread.php?t=202605&page=30#298]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298")_

Also includes some general notes on configuring your modem router to assign static or reserved IP addresses to each PC on your network.


**_Printing to a printer attached to an Windows PC_**

I copied this HOWTO from an Ubuntu topic, but cannot find it.  Credit goes to the unnamed contributor.

I use an HP Deskjet 930C.  Note that the HPLIP HP Management program cannot be used since it does not cater for printers connected to windows PC's.

Using Synaptic make sure samba, samba-common and Smbclient are installed.

System>Administration>Printing>New Printer

Network printer; Windows Printer (SMB)

If Username / Password box comes up, close down (not needed).

HOST: The name of the Windows PC to which the printer is connected &#8211; e.g mine is &#8220;HOME&#8221;.

(This can be found on Windows PC &#8211; Start > My Computer > My Network Places > Microsoft Windows Network > Mshome).

Printer: HPDeskjet
Forward.
Select the Manufacturere and model eg HP Deskjet 930C
Forward
Description: Use the same name as in Name box
Apply

Since the Firewall has already been enabled, it should be possible to print from Ubuntu to Windows PC without disabling it.


**_Setting up the Synaptic Touchpad_**

Out of the box I found the touchpad to be extremely sensitive and the following HOWTO installs an app to set it up.

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

Touchpad can be set up via System > Preferences > Touchpad


Many thanks to the topic contributors for the linked posts.=D>

---

