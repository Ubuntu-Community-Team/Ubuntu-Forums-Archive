---
title: "[SOLVED] wireless???"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by kewlfuzz on 2008-03-21
hello all,
I'm a new user, and could really use some help here, i'll try to describe my issue fully.

I have a linksys Model No. WPC54G (no ver the linksys guy said ver 1)wireless adapter (fcc id: PKW-WPC54G-2),

i have been using ndiswrapper to try and use a WPC54G ver 2 (DIFFERENT CARD) using this guide:

[http://blog.eksfiles.net/2007/12/30/...-ubuntu-gutsy/](http://blog.eksfiles.net/2007/12/30/...-ubuntu-gutsy/)

but then i realised that my ver 2 card (DIFFERENT CARD) never worked on windows either,

so try my ver 1 card and ubuntu said it was using a broadcom b43xx or bcm43xx chipset needed proprietary driver, would you like to install? i said yes and did the restart and i could see the network! i know the wep key i've checked it over and over but everytime i try to connect it keeps coming back and asking me for the wep key again and again never quite connecting, i get syslogs like this:

Mar 21 18:50:37 super-duper kernel: [ 489.612000] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c :1112
Mar 21 18:50:37 super-duper last message repeated 7 times
Mar 21 18:50:37 super-duper kernel: [ 489.612000] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c :1114
Mar 21 18:50:37 super-duper last message repeated 3 times
Mar 21 18:50:37 super-duper kernel: [ 489.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 21 18:50:39 super-duper kernel: [ 491.412000] pccard: card ejected from slot 0

is there a good easy way to fix this? i've been trying to ndiswrapper the driver i downloaded from linksys(not sure if this is the right approach or not) but when i try
sudo ndiswrapper -i <filename>
terminal returns:
driver lsbcmnds is already installed

do i just need to uninstall lsbcmnds, and try the files i have? how would i do that? or is there some other little tweak or command line i can use to fix these issues? i mean it seems to work kind of, other than the whole asking for wepkey repeatedly and never actually connecting the the network.

thanks a lot for showing ubuntu love,
kewlfuzz

---

### Post by wobbiebobbie on 2008-03-22
**This post could be related to an Ubuntu bug filed at**: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I work for weeks to get my linksys wpc54g ver4 working no go I had to get a card that will work on ubuntu heres a link of cards that will work

---

### Post by timbounceback on 2008-03-22
apparently updating the firmware fixes it: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

---

### Post by kewlfuzz on 2008-03-22
thanks for the suggestions guys i tried using the restricted drivers manager and installing bcm43xx but it was able to see however never connect to the network

i was able to get ndiswrapper working after reinstalling it uninstalling the restricted driver and blacklisting a bunch of things just to be safe i blacklisted
blacklist bcm43xx
blacklist acx
blacklist ssb
blacklist b43

thanks to all muh homies showing the ubuntu love
kewlfuzz

---

