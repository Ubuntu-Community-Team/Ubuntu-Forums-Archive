---
title: "Issue w/ Linux Mint Wifi Drivers"
date: 2011-05-06
forum: Any Other OS
---

### Post by DevinJCan on 2011-05-06
Hello and thanks for reading my thread,
[LEFT]I have recently purchased a Toshiba Satellite C655D-S5138 running windows 7 and I have installed Linux Mint 10.10 gnome. I am having an issue with the Wireless networking in Mint. I have a "Realtek RTL8188 Wireless LAN 802.11n PCI-E NIC" wireless card. I have attempted to (1) run system preferences/hardware drivers application and to (2) load the windows driver in mint through the "windows wireless drivers" application in the control center in mint (the problem I am having there is that mint is asking for a .inf driver and I have only come up with a .sys {I am assuming that is the difference between windows xp & 7 drivers}). Any solutions/suggestions will be appreciated! I thank you for your time.  


just found this: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

...not sure if/how it will work.




:popcorn:[/LEFT]

---

### Post by Perfect Storm on 2011-05-07
Moved to Other OS/Distro Talk.

Also read: [http://ubuntuforums.org/showthread.php?t=1721564](http://ubuntuforums.org/showthread.php?t=1721564)

---

### Post by varunendra on 2011-05-07
> **DevinJCan said:**
> I have a "Realtek RTL8188 Wireless LAN 802.11n PCI-E NIC" wireless card. ...... the problem I am having there is that mint is asking for a .inf driver and I have only come up with a .sys {I am assuming that is the difference between windows xp & 7 drivers})
[LEFT] 
just found this: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

...not sure if/how it will work.[/LEFT]

Hi, and welcome to the forums.

First about the windows driver: An 'inf' file is just an 'information' file, not a driver, which includes device details, settings and name/address/version of the required driver file(s). The 'sys' file is the actual driver, but is useless without the settings info included in the 'inf' file. That's why the installer is asking for 'inf', but it will then need that sys file which the inf file will tell it to look for.

Where did you get that 'sys' file? There 'should' be an inf file with it. Once you provide it, the installer 'should' automatically recognize and use the 'sys' file (driver) with recommended device-settings.

Next, the link you provided: For 8188CE model, it says-     > Driver available from Realtek's site, but must  be compiled by user (instructions included).  Alternatively, as of this  writing (Jan 2011), [COLOR=Red]**there is a PPA available [here]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")  with a precompiled driver, eliminating the need to recompile after  every  update.  Instructions are available on the site if you are  unfamiliar with the process of adding a PPA, and the package you will  need to install is [COLOR=DarkRed]rtl8192ce-dkms[/COLOR].**[/COLOR] 


The suggested link for the PPA is the easiest method to install the driver from synaptic. Further, as the instructions on the linked launchpad page suggest, just open Synaptic Package Manager > Settings > Repositories > open 'Other Software' tab > click 'Add' button, and copy paste **ppa:lexical/hwe-wireless** in the 'APT' line field.


Then close the box, click "reload" button on Synaptic's toolbar, and type [COLOR=Red]**[COLOR=DarkRed]rtl8192ce-dkms [/COLOR]**[/COLOR]in the 'search' box. It should come up in the package list. Just click and select to install it. Done!

---

### Post by DevinJCan on 2011-05-10
Thank you Varun!!! I truly appreciate the guidance. The driver is up and running. I have a few other issues to work through, but that was the big one. 1,000 Thank Yous! 

 "I am what I am because of who we all are."

:grin:_******_

---

