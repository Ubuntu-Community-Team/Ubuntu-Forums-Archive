---
title: "Really New Beginner"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by kitar on 2007-03-16
Good evening everybody...

Finally i installed UBUNTU and everything seems to be Ok.

First step to leave WIndows is given.

However i have some problems with my connection to the Internet

My Questions are:

What is a terminal?

How can i fix my problem with my wireless connection ?
 I have allready setup the connection with the hexadecimal key , but i am not so sure that my network adapter is Ok. it's a surecom 108Mbps Wireless Adapter Network, and i can't find any drivers for Ubuntu.

How can i install new peograms and there is a lot of them on Internet.  I really want to leave the Windows and i am finding the Linux way of working in order to unplug WIndows. 

Can somebody help me? 

Would appreciate very much

---

### Post by bobplano on 2007-03-16
the terminal is like the command line for windows. i don't know about your wireless (i havent set it up either). an easy way to get programs is aptitude or synaptic

---

### Post by metroknight on 2007-03-16
Hi,

I'm new also but try these suggestions.

You can find the terminal in your applications-accessories. This is to allow you to use text commands ( I think some people refer to it when they mention command lines?).

Have you looked in your System-Admin-Networking (or is it Network tools) and seen if your computer has detected your card? If it hasn't then you might want to search for Ndiswrapper, wireless in the forum.

Installing programs - still learning that myself.

---

### Post by Griffiss on 2007-03-16
The terminal is a window you can use to type commands into your system. In the menu on the top bar, click on Applications then Accessories then Terminal.

I'm new myself so dunno how much help I can be to you with wireless - although I spent 3 days trying to get mine working so hopefully learnt a thing or two!

Firstly, check if your system recognizes your wireless device - type ```
iwconfig
```into the terminal. Don't worry, this doesn't change anything, just displays some information.

---

### Post by igknighted on 2007-03-16
> **kitar said:**
> Good evening everybody...

Finally i installed UBUNTU and everything seems to be Ok.

First step to leave WIndows is given.

However i have some problems with my connection to the Internet

My Questions are:

What is a terminal?

How can i fix my problem with my wireless connection ?
 I have allready setup the connection with the hexadecimal key , but i am not so sure that my network adapter is Ok. it's a surecom 108Mbps Wireless Adapter Network, and i can't find any drivers for Ubuntu.

How can i install new peograms and there is a lot of them on Internet.  I really want to leave the Windows and i am finding the Linux way of working in order to unplug WIndows. 

Can somebody help me? 

Would appreciate very much

1) A terminal is a text only prompt to enter commands directly to the computer.  Typically in linux there is a GUI way of doing something and a terminal way.  On the forums, you will usually get the terminal way because it is easier to post and is always the same (GUIs differ with gnome/KDE/Xfce etc).  To get to it, go to Applications->Accessories->Terminal.  Basically  think of it as a DOS prompt, but infinitely more powerful.

2) Can you post the results of the commands "lspci" and "iwconfig"?  Type them in the terminal.

3) New programs are installed via Synaptic or Add/Remove programs.  You don't browse the web yourself, Synaptic has a server it connects to that has like 20,000 programs available to you.  If there is something specific you need that is not in Synaptic, there are ways to get it... but thats a last resort.

---

### Post by kambei on 2007-03-16
> **kitar said:**
> Good evening everybody...
My Questions are:

What is a terminal?

How can i fix my problem with my wireless connection ?
 I have allready setup the connection with the hexadecimal key , but i am not so sure that my network adapter is Ok. it's a surecom 108Mbps Wireless Adapter Network, and i can't find any drivers for Ubuntu.

How can i install new peograms and there is a lot of them on Internet.  I really want to leave the Windows and i am finding the Linux way of working in order to unplug WIndows. 


The terminal gives you command-line access while in the GUI... You can find the Gnome terminal program bundled with Ubuntu under 'Applications->Accessories->Terminal'

Synaptic (System->Synaptic) is a nice point-n-click frontend to the application archives... lots of info on the Ubuntu sites for setting up and using it to install programs.

I would also recommend grabbing some 'dead-tree' aka books to get you started... I gave out a few copies of 'Ubuntu Linux For Non-Geeks' by Rickford Grant as Christmas presents, and all the recipients seemed to like it and are running Ubuntu now...

Welcome... and good luck!

---

### Post by teaker1s on 2007-03-16
Applications>Accessories>Terminal
terminal allows us to type commands to tell ubuntu what to do.
your wireless may require either configuring or something called ndiswrapper and windows drivers.
How about we try bringing up terminal and typing 
```
iwconfig
``` and post output-see if we can see if wireless is running and unconfigured

beaten to it, my isp having problems:(

---

### Post by raja on 2007-03-16
Welcome to Ubuntu. Go to Applications --> Accessories --> Terminal and there you have the terminal. Dont worry too much about it for the present, though. Go to System --> Administration --> Synaptic Package Manager. You will have to enter your password to use it with administrator rights. You can see listed a lot of applications that are just a click away from installing ! Choose what you want and ask Synaptic to install it for you. You can also enable the Universe repository from Synaptic to allow access to more applications. 
For starters, type ```
iwconfig
``` in the terminal and paste the output here for people to help you with the wireless.

---

### Post by kitar on 2007-03-17
Thanks everyone for your kindly reply:

I made "iwconfig" and that's what i get

[I]lo         no wireless extensions


wifi0     no wireless extensions


ath0     IEEE 802.11g   ESSID:"CASA"
           Mode:Managed    Frequency:2.447 Ghz    Access point: Not-Associated
           Bit rate: 0 Hb/s     Tx-Power: 16 dBm      Sensitivity=0/3
          retry:off    RTS thr:off      Fragment thr:off
          Power management:off
          Link quality:0/94   Signal level=-95 dBm    Noise level=-95 dBm
          Rx invalid nwid:0    Rx invalid crypt:0      Rx invalid frag:0
          Tx excessive retries:0    Invalid misc:0    Missed beacon:0

eth0    no wireless extensions

sit0      no wireless extensions [/I]


:( 

i guess that something is wrong 

for the all scenario i have a wireless router and a pcmcia wireless in my laptop

Today i noticed that is very boring to make a command and have to write it all the way because Windows can't read UBUNTU. 

when i tried to print it i noticed that my printer "Brother Laser Jet HL2070N" is not configured. Tried to reach drivers for Ubuntu, but didn't get any luck.

Maybe i reached the club where everyone that wants to switch from WIndows belongs.
Until now and beginning here is OK and Good. 

So, let's keep on going and see if someone can send me an help for those drivers for my printer also

---

### Post by teaker1s on 2007-03-17
ath0     IEEE 802.11g   ESSID:"CASA"
           Mode:Managed    Frequency:2.447 Ghz    Access point: Not-Associated
           Bit rate: 0 Hb/s     Tx-Power: 16 dBm      Sensitivity=0/3
          retry:off    RTS thr:off      Fragment thr:off
          Power management:off
          [COLOR="Red"]Link quality:0/94   Signal level=-95 dBm    Noise level=-95 dBm[/COLOR]
          Rx invalid nwid:0    Rx invalid crypt:0      Rx invalid frag:0
          Tx excessive retries:0    Invalid misc:0    Missed beacon:0

looks like card is alive, if you can plug into an ethernet cable to get internet

```
sudo apt-get install network-manager-gnome
```

now on your desktop panel you want to click -
system>administration>networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by decentnnice on 2007-05-17
hi m facing the same problem ...m also new to Ubuntu ... but i know a little bit abt Terminal ... 

The results of Lspci 

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
0000:00:0f.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 01)


& the result of iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Kindly tell me how to  install my Wireless LAN CARD

---

### Post by freesitebuilder on 2007-05-17
This site is a good introduction to using Linux commands in the terminal
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

