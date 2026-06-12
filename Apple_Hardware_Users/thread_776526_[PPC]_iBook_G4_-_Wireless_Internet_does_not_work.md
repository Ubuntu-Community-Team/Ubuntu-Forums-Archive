---
title: "[PPC] iBook G4 - Wireless Internet does not work"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by ZomGie75 on 2008-04-30
My iBook connects to my Airport, but doesn't have any internet connection.

I got to "Hardware Drivers" and it shows "Broadcom B43 wireless driver [  ]  in use"
I click the box to enable it and a box pops up:
> 
**Broadcom B43 wireless driver**
While this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system.  Your hardware will not work without the firmware.

I then click "Enable", and it downloads and installs the drivers.  So I am now connected to my airport, but there is not internet connection.

The internet connection works perfectly on my Mac OS X partition.

What do I need to do now to get the internet working?

lspci:
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

```

---

### Post by ubuntubrian on 2008-04-30
I have a G3 Lombard and a Broadcom PCMCIA wifi card as the laptop has no airport. I was getting the exact same messages, had the network showing up and the whole 9 yards. I ran"dmesg" in a terminal and the output showed the error which was needing a firmware update-just like your problem. 
The output also had the website to download the update and a link to instructions to install it. Instructions were a bit tough for my skills but it worked perfectly and I have internet.
I can't go thru the install instructions as I just followed them on the site. If I can do it so can you.
Good luck

:popcorn:

---

### Post by ZomGie75 on 2008-05-01
Wow, I just randomly turned my laptop on, loaded Pidgin, and the wireless suddenly worked.  Sweet!

---

### Post by renichms on 2008-09-21
So has anyone figured out yet how to get an Airport (not Extreme) card working in Ubuntu?  I've been checking online for hours now and asking everywhere possible and getting absolutely nowhere.  Even been looking into replacing Ubuntu with another distribution but it seems there isn't a single soul that knows how to get Linux to work with an Airport card and that is an absolute requirement for me to use it (the particular distribution).

RN

---

### Post by ubuntubrian on 2008-09-21
I'm using my TiBook G4 and airport has worked since ubuntu 4.something (warty?) I am currently running Hardy and networkmanager works flawlessly using my airport card. Do you have networkmanager installed? It should detect your card and networks and connect.
Since networkmanager connectivity is much easier. It came out in Dapper, 6.04

---

### Post by renichms on 2008-09-21
I have 8.04.1.  About 3 minutes ago, I got it to seem to work.  The connection is too slow to use Gmail (in Ubuntu...works fine in Mac) but it connects now.  It seems that when I put in the SSID, it added that name to one domain slot but not enough.  Just putting the SSID into the other domain slot seems to have it functioning but we'll see if it lasts through tomorrow too.  Hope so...

RN

---

### Post by ubuntubrian on 2008-09-22
At least it works a bit.
Again,networkmanager just finds networks, anywhere, for me and I choose them and connect. No ids or anything. I have my network settings set to DHCP andall connections are automatically found and done. Do you have networkmanager installed? I use gmail and a regular ISP too and speed is good for either. I use networkmanager on my old G3 Lombard and other thatn installing a driver update it works great too.

---

### Post by renichms on 2008-09-22
System->Administration->Network.  Brings up window called "Network Settings".  Wireless connection, wired connection, point to point connection in that.  Going to test some new settings again...keep domains but use the other wireless SSID (since it uses the first to assign IP).

Let's call the router that is running DHCP and a wireless network router A.  Let's call the Airport router B.  Here is the setup that had Ubuntu on a very slow connection (that refuses to show up as a connection anywhere):  SSID is set to A (set to WPA without a password since a no password/key option is unavailable and Ubuntu doesn't support WPA), Domain name is set to A, it automatically received from A the DNS servers and A as the Search Domain.

According to all network info I can get from the Mac OS when it's up, here's the faster connection that works when started as Mac OS (in form like the Linux connection above):  SSID is set to B (B takes WPA or WPA2 and this computer only wants to function on WPA), Domain is set to A (although this is not a setting I manually change, it is automatically set behind the scenes and only reported to me later when I really dig for settings) and it receives DNS servers and search domain of A from A.

When I try to set it up identically to the Mac setup, Ubuntu refuses to recognize that there is a network of any kind.  Ubuntu seems unable to connect to B, whether it's because it does not support WPA/WPA2 or is something else, I don't know.  Right now, it's connected to A and barely sustaining enough of a connection to be considered on par with dial-up.  It does fine if I stretch a cable across the house at about waist height but that's not exactly an option.

So is there something wrong with Ubuntu that keeps it from using WPA/WPA2 or, more specifically, keeps it from using Airport networks?  The Airport is the only consistently strong, reliable signal here (router A is wonderfully spotty in its wireless coverage), so shouldn't there be some way to connect to it?  The computer I'm on now is farther away and connects to it no problem.

This is very frustrating.

RN

---

### Post by cyberdork33 on 2008-09-22
> **renichms said:**
> System->Administration->Network.  Brings up window called "Network Settings".  Wireless connection, wired connection, point to point connection in that.  Going to test some new settings again...keep domains but use the other wireless SSID (since it uses the first to assign IP).
You should not use that utility (In fact, I think they are planning to remove it in Intrepid). Set your card back to roaming mode and use the network manager icon near the clock.

---

### Post by ubuntubrian on 2008-09-22
Network-manager is not the same as network settings. Check it out in Synaptic and install it. The other option is Wicd which I don't use because network manager does it all for me but some say Wicd is better:
[http://brainstorm.ubuntu.com/idea/2591/](http://brainstorm.ubuntu.com/idea/2591/)
for some insight. Wicd is not in the repositories so I guess you need to download it and install it.
Again, network-manager finds the network and connects either wireless or ethernet. It supports WPA, WEP and other security protocols.
I would try that avenue first.

---

### Post by renichms on 2008-09-22
cyberdork33, you are magic.  I've tried using that a number of times before and it's only options were "wired network" and manually configure.  Now I go back and it allows me to enter a network name and pick up a grand total of 1% signal (it should be a lot more).  So the connecting to a network thing works right now, I just need to find a way to add in the ability to use WPA so I can get the stronger network.

I'm going to check this Belkin router to see if somehow it's just not up to full strength or something.

RN

EDIT:  Every 2 seconds or so, this network cycles between 2% signal and 97%.  It did this with the Macs and now with Ubuntu (but not YDL).  Any ideas what would make a router do that?

---

### Post by ubuntubrian on 2008-09-22
right click (with a 3 button mouse or F12 on my powerbook) on the network manager icon and you will get a list of available networks and the ability to set the security, WPA, WEP or whatever. I have used it many times at other places that had WEP or WPA and it worked great. It always works. 
I checked out: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
adding it to the repositories (and changing Gutsy to Hardy) gave me WICD in Synaptic as an installable package. Installing it would remove network manager so I didn't do the install.

---

### Post by renichms on 2008-09-22
> **ubuntubrian said:**
> right click (with a 3 button mouse or F12 on my powerbook) on the network manager icon and you will get a list of available networks and the ability to set the security, WPA, WEP or whatever. I have used it many times at other places that had WEP or WPA and it worked great. It always works. 
I checked out: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
adding it to the repositories (and changing Gutsy to Hardy) gave me WICD in Synaptic as an installable package. Installing it would remove network manager so I didn't do the install.

Didn't work.  Editing the wireless networks doesn't do anything because it only shows the spotty network it's already on.  Since the option to connect to other wireless network does not support WPA, I can't connect to the Airport to start with, so it doesn't show up in the list of networks and I can't edit it where there actually is the WPA option.  How do I get it to add WPA the first time I'm adding the network?  Seems to be a bit odd that they'd allow every WEP known to man and LEAP but no WPA the first time around, when it matters.

Looking through all the threads I can to see if anyone succeeded in adding WPA support to Network-Manager.

RN

EDIT:  Found one thread where the person dropped encryption and just used MAC address filtering to keep others out.  I could do that but then everything would continue being passed in the clear from the Linux machine.  Looking into Wicd to see if it'd do the job and can actually be installed too (had problems with YDL not wanting to install anything, so somewhat wary with Ubuntu).  Only problem with Wicd is their site gives directions on how to download it to Ubuntu...I can't do that.  Is there some other way to get it and slap it on the computer?  Then, if I can find a way to download to flash drive and then put it on Ubuntu, how do I get it to install since installing programs in Linux seems to be far more complex than in other systems?

EDIT2:  Still nothing.  No luck figuring out how to get wicd in or to do anything about changing networks.  Any idea if Fedora supports WPA/WPA2 out of the box?

---

### Post by renichms on 2008-09-22
Wicd is installed and it looks great.  However, it has absolutely nowhere to select WEP, WPA or WPA2 and no way to enter a password either.  I'm about ready to throw in the towel.  I am not a programmer and I loath having to manually create text configuration files to make things like this work when they should work as advertised to start with.

I'll give it a few more days to try and figure out why Ubuntu doesn't support WPA/WPA2 or connect worth a crap, then I'll install Fedora over it and give that a shot.  If that fails, I guess I could just convert the HDD back into one Mac partition.

If anyone out there is using a regular Airport card with an Airport wireless network with WPA/WPA2 and SSID off, PLEASE tell me how you got Ubuntu to connect.  I'd keep posting in the networking section about this but there's absolutely no hope of anyone paying attention to it.

RN

---

### Post by cyberdork33 on 2008-09-22
> **renichms said:**
> If anyone out there is using a regular Airport card with an Airport wireless network with WPA/WPA2 and SSID off, PLEASE tell me how you got Ubuntu to connect.  I'd keep posting in the networking section about this but there's absolutely no hope of anyone paying attention to it.
I have an original Airport card in my old G3 iBook, but I have only ever gotten WPA to work in Mac OS. I don't think the card supports WPA in the traditional sense, and Mac OS did some kind of software addon to allow for WPA...

(plus it is really picky about my router's settings so that it will connect over WPA...)

---

### Post by renichms on 2008-09-22
> **cyberdork33 said:**
> I have an original Airport card in my old G3 iBook, but I have only ever gotten WPA to work in Mac OS. I don't think the card supports WPA in the traditional sense, and Mac OS did some kind of software addon to allow for WPA...

(plus it is really picky about my router's settings so that it will connect over WPA...)

In the iMac, it refuses to do WPA2 but gets on fine with WPA (when in Mac OS).  Everything I read about most versions of Linux say they support WEP, WPA and WPA2 out of the box but I can't get Ubuntu to work with WPA/WPA2 on a closed network.  I also can't afford to keep giving time to trying to configure Ubuntu so it'll be useful.  3 days without connecting like it should is about the limit for me.

I don't want to come across as rude but it may sound it but...  Either it works or it doesn't.  So far, it doesn't and no other software or config changes have helped.  I think Ubuntu just doesn't support encryption on wireless connections.  I'm looking at other distributions to see if they really do support wireless encryption out of the box and if so, I'm probably just going to switch.  Ubuntu is cool and all but it isn't worth all this effort, especially considering it also throws errors on startup and no one has been able to help with those either.

These kinds of issues are what scare normal users away from Linux.  If I have troubles setting it up, a normal user has absolutely no hope.

RN

---

### Post by cyberdork33 on 2008-09-22
> **renichms said:**
> Either it works or it doesn't.  So far, it doesn't and no other software or config changes have helped.  I think Ubuntu just doesn't support encryption on wireless connections. 
Well, I am trying to say that I don't think your hardware supports it under Linux....

Ubuntu certainly does support WPA/WPA2 out of the box... I have used it several times, just not with the same card as you have... 

I know you are frustrated, but do not make Ubuntu out to be worse than it is. It is true that it is not working for you, but that does not mean it doesn't work for everyone else... Also, please remember that Ubuntu is not officially supported by canonical anymore. It is a community-supported release now, so there are additional shortcomings with the PPC edition.

I hope you find the distro you are looking for. Good Luck!

---

### Post by renichms on 2008-09-22
Know of any distributions that would support an 802.11b connection to a closed network with at least WPA?

RN

---

### Post by cyberdork33 on 2008-09-22
> **renichms said:**
> Know of any distributions that would support an 802.11b connection to a closed network with at least WPA?
Nope, sorry. 

P.S. I just noticed you are also in Huntsvegas. Great place to live, huh?

---

### Post by renichms on 2008-09-22
> **cyberdork33 said:**
> Nope, sorry. 

P.S. I just noticed you are also in Huntsvegas. Great place to live, huh?

It's okay.  I looked for a job for 2.5 years in Birmingham and had to sell my house, move in with parents and borrow money to get another degree so a recruiter somewhere will suddenly become literate.

RN

---

### Post by gaussian on 2008-09-22
> **renichms said:**
> In the iMac, it refuses to do WPA2 but gets on fine with WPA (when in Mac OS).  Everything I read about most versions of Linux say they support WEP, WPA and WPA2 out of the box but I can't get Ubuntu to work with WPA/WPA2 on a closed network.  I also can't afford to keep giving time to trying to configure Ubuntu so it'll be useful.  3 days without connecting like it should is about the limit for me.

RN

Ok, I have pretty similar hardware as you do (Airport original card). Here are the facts as far as I understand them:

1) Ubuntu (and many other Linux distros) support WPA and WPA2 out of the box with many hardware configurations. The issues is whether the linux driver for the network chip supports them. I use WPA2 daily with Ubuntu.

2) For Airport it does not. There is a hacked driver that people have been successfully used in Intel hardware. I and as far as I can tell, no one else, has been successful in getting it work to work on a PPC hardware. If anyone manages do that it would be great. 

3) You could buy a USB stick wireless card that is Linux compatible and get WPA2 to work with minimal hacking.

---

### Post by renichms on 2008-09-22
Thanks for the suggestion.  I may repartition the entire drive and give Ubuntu a slightly smaller space and then enough space for another Linux distribution and keep Mac OS about same size.  Then I have one free partition to experiment with and the computer will, within a few years, be connected directly with a cable so either someone will have it done by then or the cable will have to do.  Until then, I think Ubuntu gets shelved.

RN

EDIT:  Fedora 9 did the trick.  Typing this in Fedora now while the other computer backs up to an external drive.  Thanks for trying to help with Ubuntu!

---

