---
title: "Trying to work wireless adapter and screen resolution"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Drethon on 2007-07-30
I am completely new to linux and trying to get my WPC54GS wireless to run and my Dell Inspiron 1100 screen resolution up proper.

I haven't had time to look up stuff for the screen yet but I've seen information for the wireless to use ndiswrapper to install the drivers but cannot locate ndiswrapper anywhere in synaptic.  I downloaded the .tar for ndiswrapper but when I try to "make install" it I get the following errors which I don't even know where to start looking for answers to:

mkdir -p /lib/modules/2.6.20-15-generic/misc
mkdir: cannot create directory `/lib/modules/2.6.20-15-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/linggm/Downloads/ndiswrapper/ndiswrapper-1.47/driver'
make: *** [install] Error 2

Help please?

---

### Post by Drethon on 2007-07-30
Doing a brief google search on this issues results in mostly people stating this (ndiswrapper) has been resolved long ago and people should search for the resolution.  Well so far I can't find the resolution and I'm searching though an ittybitty screen that can't see much so help would be appreciated.

---

### Post by crjackson on 2007-07-30
[http://ubuntuforums.org/showthread.php?t=483548]("http://ubuntuforums.org/showthread.php?t=483548")

I'm very mcuh a noob and I had a hell of a time getting my wireless to work - Look at the thread in the link above and you'll see this is not especially easy but doable.

I could never get a PERFECT install of ndiswrapper but I did finally get it.

An easier method (I'll probably get flamed for this) is to download automatix (do a google search for the home page) and let it install it for you.  I've used automatix to install many of my programs and don't really have anything bad to say about it.

I realize this may not be what you wanted to here but it's the best I can do.

Just hang in there and keep banging away at it.  You'll get it working...

I have screen resolution issues of my own on some of my computers too, so I can't really give you direction on that one.

---

### Post by Brightbelt on 2007-07-30
Hi,
I'm no expert on ndiswrapper per se, but when I see a 'permissions denied' in my error code, I go back and make sure I've put 'sudo' in, eg 'sudo make install' 

Read the Install file within your Ndiswrapper folder - it may be worth first doing an uninstall of ndiswrapper before proceeding again.. .the Install file should have that instruction included. Mine did. 

I hope this helps,

Frank B.

---

### Post by anewguy on 2007-07-30
If you can't find ndiswrapper, try putting in the LiveCD (don't boot from it, just put it in the drive while in Ubuntu).  It should come up and say something to the effect of a volume with software packages has been detected and ask if you want to run package manager - answer yes.  When the package manager comes up, search for ndis  and you will find ndiswrapper.  You need to install the utilities with it.:)

For screen resolution, try the things in these posts:

[http://ubuntuforums.org/archive/index.php/t-190022.html]("http://ubuntuforums.org/archive/index.php/t-190022.html")

[http://ubuntuforums.org/showthread.php?t=237626&highlight=dell+inspirion+1100]("http://ubuntuforums.org/showthread.php?t=237626&highlight=dell+inspirion+1100")

It looks to me like at a minimum you need to have your system bios at a certain level, and I would think installing one of the video drivers as outlined in the posts should do it.  


Please post back after you've tried a couple of those things and let us know what happened and if you need more help.:)

---

### Post by Drethon on 2007-07-30
It would help if I had a working cd drive :).  I suspect part of my issues is apt-get is looking for the cd drive and nowhere on the network.  Any suggestions on how I can get it to look at the network if this is the problem?

---

### Post by anewguy on 2007-07-30
If you can get on the network, then start up synaptics package manager, then click settings and then repositories.  Since I don't know where it comes from (but it shows in my list), be sure all are checked except "download from source" then close the repositories window to get back to the main package manager screen.  Search for ndiswrapper via the search button.  Be sure that ndiswrapper-common and ndiswrapper-utils-xxxxx (whatever shows - for me it is 1.9) are marked for installation, then click apply to install them.:)

---

### Post by Drethon on 2007-07-30
I found the package, I was ignoring the popup that said to press reload after changing servers... wups. ndiswrapper is now working :) I'll be back if I have further problems.

---

### Post by anewguy on 2007-07-31
I also found this that might help with your resolution problems:

[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

:)

---

### Post by Nudgeworth on 2007-07-31
> **anewguy said:**
> I also found this that might help with your resolution problems:

[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

:)

I was using this thread earlier and learnt a lot. how ever it didn't solve the resolution problem with my Intel graphic's card.  Then at the end o f the thread I found this

 
"sudo apt-get install xserver-xorg-video-intel"

 Enter this in a terminal (without the quotation marks) push enter, then when it's finished re-boot. 
 It worked for me :)

---

### Post by Drethon on 2007-07-31
Resolution now working, anewguy's links worked.  Still having issues with the wireless even with ndiswrapper installed, got the following message out of dmesg:


[ 535.274947] ndiswrapper: driver lsbcmnds (Cisco-Linksys ,LLC.,02/19/2004, 3.50.21.11) loaded
[ 535.275964] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[ 535.275987] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 535.276068] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 535.282793] ndiswrapper: using IRQ 11
[ 535.605535] wlan0: ethernet device 00:13:10:3e:ff:a3 using NDIS driver: lsbcmnds, version: 0x332150b, NDIS version: 0x500, vendor: '', 14E4:4320.5.conf
[ 535.606122] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[ 535.710064] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[ 535.853894] ADDRCONF(NETDEV_UP): eth1: link is not ready

???

---

### Post by BC7333 on 2007-07-31
Noob here, but [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) resolved my wireless problems.

good luck~!

---

### Post by Drethon on 2007-07-31
I tried wicd but it would not find my hidden network or connect to a non-secured network in the neighborhood.  Thanks though

---

### Post by BC7333 on 2007-07-31
> **BC7333 said:**
> Noob here, but [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) resolved my wireless problems.

good luck~!

Did you try 1.3.3?

Am on an unsecured network now.  Believe it or not if your router is too close you might have to move away from it.. 20 ft or so for it to connect.

---

### Post by anewguy on 2007-08-01
What does ndiswrapper -l  <--lower case "L" return?

---

