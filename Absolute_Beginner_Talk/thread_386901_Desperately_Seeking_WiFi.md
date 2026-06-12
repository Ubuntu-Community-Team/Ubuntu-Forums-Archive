---
title: "Desperately Seeking WiFi"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Hraefn on 2007-03-17
Howdy all,

So, this is my reach for help.  I've done all I can before posting here, but I'm at my wit's end. 

I have managed to load 6.1 Edgy on my Gateway 400SD4 Laptop.  About a year ago, I installed a mini-pci wifi card into this machine, as I wanted to enable wireless capabilities.  I wasn't thinking too far down the line, and have now realised the absolute beauty a linux-capable card would be...

It has the Atheros chipset, and the vendor I bought it from has a madwifi driver that I have dutifully downloaded, installed all of the applications needed to peform the make and install.  I have prayed to the WiFi Gods for their approval, but to no avail.

I also have tried to do the ndiswrapper thing, using the windows driver files that I've obtained from the vendor, too.  In this driver file, there are three folders - Windows 9X, Windows 2K, and Windows XP (each containing essentially the same driver, but adapted for each platform).  Windows setup recognises which files are required for the platform they are being installed upon, however, I'm not sure I'm using the right one for Linux.  I assumed the WinXP driver files wouldn't work, so I stuck with the Win9x files.  

No luck

I tried the other two versions of this, and again, it's not working.

I've tried the madwifi route, again, getting madwifi-0.9.2.1 files, doing the make and install with that. 

If you, you special person you, know how to help me get even further away from Windows, and get my Ubuntu working over the airwaves, I will be eternally greatful.

Stuck in XP-land,
Hraefn

---

### Post by Josey on 2007-03-17
I've had trouble with a card with the atheros chip too.  Luckily I found a card laying around that worked out of the box.  I don't have any advice for you except to support hardware manufacturers that provide linux support.  We wouldn't have these problems if they showed linux some love.  :)

Sorry for the useless reply.

---

### Post by SactoBob on 2007-03-17
Atheros is one of the good manufacturers who does support Linux.  You could argue that madwifi is the best wireless implementation our there for Linux.  I am not the only one who thinks so.

Some Atheros usb cards are not supported by madwifi, but almost all mini-pci cards are supported. Yours being over a year old, give madwifi a shot.  If you can run madwifi, there is no reason not to IMO.  

Ndiswrapper is great for cards that have no native driver, or a poorly performing native driver.  Your Atheros card should virtually work out of the box, or you may need to install the restricted modules package package with the madwifi driver and HAL (hardware abstraction level) code.  If those are present, and the card is supported, it just works.

Are you in a place where you can do a clean install, ideally with wired access to internet?  You might consider that.

The problem is that you have tried both madwifi AND ndiswrapper.  You don't want two drivers fighting over the same Atheros device.  You need to use one or the other.  I am going to talk about madwifi since I consider it easier and am more familiar with it.

First, identify what card and chip you have.  From the console, type lspci and check the output, look for the Line with Atheros in it (you could pipe lspci to grep Atheros for fancy, i.e. lscpi | grep Atheros)

Also, try to find the model of card you have, and with this info, visit madwifi.org to see if somebody has got your card working.

If you don't do a clean install, make sure that ndiswrapper no longer possesses your Atheros card.  Check the ndiswrapper docs to remove that driver.

Have a wired internet connection, go to Synaptic Package Manager, enable all repositories, and search for the latest madwifi driver - I think in the linux restricted modules package (non-free package, so make sure that all respositories are enabled)

If you are not sure how to configure your card, or are lazy like me, also install network -manager-gnome, which will walk you through your connections when you click on its icon.

When you reboot, your card should be active and ready to configure.

---

### Post by Hraefn on 2007-03-18
Thank you for the much-appreciated guidance.  I thought there might be a conflict of ownership over the card, but being a NOOB, I have an exemption from stupid things (well...almost)

I'll post later and let you know how I got on with it.  It's gorgeous out today, and I want to enjoy it with the laptop outside!

Cheers!
Hraefn

---

### Post by Hraefn on 2007-03-18
Right...replying to my own thread...looking for more advice.

I'm not able to connect to madwifi's website.  I don't know if this is because I'm in the UK, but I could surely use some advice from that site...

I've re-installed Ubuntu (nice, pristine..ahh), and downloaded the latest madwifi from SourceForge (because the madwifi site was down), and did the needed packages/make/make install thing.

2 things: Yay! the card's recognized by my system
                Nay...it's still not connecting.

I have a sneaking suspicion I need to turn on some modules, what-have-you, but because I don't know which I need to activate, and where to go for more information, here I am, asking for your guidance and help.

Recap: Atheros Chipset mini-PCI card is working, recognised by Ubuntu, but not connecting to the net...

Will do more investigating as I can, but any help anyone can offer would be much appreciated.

Cheers!
Hraefn

---

### Post by pearlie on 2007-03-18
I had the same thing happening with my (thrice cursed) Broadcom card - it was there, but I couldn't configure it with network-manager or wifi radar.  I installed [Wicd]("http://compwiz18.blackhole.cx/wicd/wb/") and (after putting in my WEP key) I was able to access my wireless network (and my neighbour's, too :biggrin: ).

---

### Post by Hraefn on 2007-03-18
More Wifi woes....

Right...so, here's what I've done:

1. Pristine install of Ubuntu 6.1
2. Nice new download of madwifi 0.9.2.1 (the latest..I think that is the version number)
3. (I think I'm missing something here...something that "turns on" the signal-reading features of the card)
4. Got rid of Network Manager, installed Wicd
5. I sometimes have a "Hidden Wireless Network," where I put in my ESSID, and when it does see this ESSID, it gives me the MAC address of my router (yay).  This, of course, has stopped working, and I no longer receive any indication that my router is out there.

I have this sneaking suspicion I need to play with the configuration of my card in Terminal, but I'm afraid, as I've killed my Ubuntu before (hardware conflict, I think...) by messing about in the Terminal.  If there is another post where these instructions might be given for an Atheros chipset card using Madwifi (chipset AR5211 802.11ab NIC), or if you know what I need to do to engage the card, your knowledge would make me gleeful again.

Cheers!
Hraefn

---

### Post by SactoBob on 2007-03-18
The madwifi site can be hard to get through to.  Keep trying.
But there is plenty of success reported with your exact chip:
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
When the chip is supported, madwifi is almost trivial to get working - only a few minutes in my experience.

I suggested getting madwifi and network manager through the repository.  You downloaded madwifi from somewhere else (for right kernel and architecture, I'm sure, and installed properly), remove your network manager and install another one that is not in the repository.

It's fun to experiment.  Ubuntu gives you the freedom to do it your own way, so I wish you success.  I'm sure that you will eventually get it working.

---

