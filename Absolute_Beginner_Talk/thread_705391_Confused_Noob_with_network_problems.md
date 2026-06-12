---
title: "Confused Noob with network problems"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Happibun on 2008-02-23
Hello.

This is not quite my first post, that is here - [http://ubuntuforums.org/showthread.php?t=202834&page=124](http://ubuntuforums.org/showthread.php?t=202834&page=124)  because I thought it was the best place to put it at the time. It's probably the right context, but I'll be waiting a while for an answer. I'd like to resolve the issue quickly because my daughter is asking for her laptop back 'Like NOW!'...

So, I'll repost here and apologise now for the bad etiquette. My brain is hurting because I'm swamped with all the info out there.

<Repost>  I am an utter Noob to Linux, having not even used a Linux machine until 48 hours ago, but always wanted to get started with it. I was given a laptop yesterday with no operating system, so I went for it and installed Gutsy 7.1. All worked beautifully except for wireless networking.

It seems that I have innocently stumbled upon the most problematic area by shear folly and ignorance. Such is life

Anyhow, this is the set up so far:
Dell Latitude 120L Laptop.
Ubuntu 7.10, Gnome.
Broadcom internal network card chipset, running with ndiswrapper.
Netgear DG834GT router with up to date firmware, was set to hidden SSID with MAC filtering on.
Now broadcasting SSID, using WPA-PSK encryption, and MAC filtering.

I have been able to connect wirelessly when the SSID was broadcast, and I had keyed the MAC addresses in to the router. However, I feel I need an extra level of security if I have to broadcast my SSID.
I would prefer to hide my SSID and I really want to keep the MAC filtering on. I'm not too bothered about WPA, the way I see it - MAC filtering is the most secure way to protect my network. I would like the laptop to be able to connect to my network when it boots, without me having to jigger about with he router or terminal each time I want to connect.

Any help would be greatly appreciated.

I'll warn you now that I am not a wireless network expert, and I'm swamped by commands and acronyms. Please be gentle with me 8-[

Thanks, Jo

---

### Post by mkzimms on 2008-02-23
from what ive read ubuntu has a few issues with trying to connect to access points with hidden SSIDs that they are working on for the hardy release.  in all truthfulness, you dont need to hide it because its really a false sense of security, anyone who wants in will have no problem finding an ap with no broadcast anyway.  you should be ok with just using MAC filtering, but please look into WPA for your own safety.

---

### Post by TeoBigusGeekus on 2008-02-23
I am not a wireless expert either but if you do a search (top right) in the Ubuntu forums you will find a lot of people complaining about Ubuntu wireless compatibility.
Now, my piece of advice:
Try to install an alternative network manager, namely WICD
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")
Since the time I replaced gnome-network manager with WICD I have noticed that my system runs more smoothly. Plus, I' ve read in some threads that a lot of people's wireless problems were solved using WICD.
Best luck!

---

### Post by Happibun on 2008-02-23
Woo!

That was quick, thanks for responding you two.

Right, I've disabled WPA-PSK encryption and got this (Windows) laptop back on line and am downloading wicd with it. Do I need both the .deb and .bz2 files? I'm a bit confused because the site does not make it absolutely clear. 

That's the problem with being so new to it, if you are not sure, you poke around and break things...

Jo

---

### Post by lswest on 2008-02-23
you'll only need either the .deb or the .tar.gz files (i recommend the .deb as it is easier to install)  you _may_ need to get internet through a wired connection when installing wicd, in case it needs more dependencies, good luck.

---

### Post by TeoBigusGeekus on 2008-02-23
Just download the .deb file and double click it. It will automatically remove the default network manager and install wicd. 
You can find some answers on the FAQ page of the link I gave you.

---

### Post by Happibun on 2008-02-23
I'm afraid I can't do a wired connection here, so I'm having to rely on a wireless windows machine to download things, and then transfer them to the linux machine with a USB key.

I have the .deb file on my Linux desktop now. Clicked it and the installer opened, but I can not install because there is conflicts with Network Manager which is already installed. :(

How do I disable Network Manager?

Thanks.

Jo

---

### Post by TeoBigusGeekus on 2008-02-23
Reboot and try again. If that doesn't work, go to terminal and type
          sudo aptitude remove network-manager
and then repeat the installation.
[http://wicd.sourceforge.net/wiki/doku.php?id=faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq")

---

### Post by Happibun on 2008-02-23
Rebooting didn't do it, so I went in to terminal with the code you suggested.

Just checking that this is what I should be seeing before I hit Y for the final time I get jittery if I se remove Gnome in the code - 

jo@EPSILON:~$ sudo aptitude remove network-manager 
[sudo] password for jo: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Initialising package states... Done 
Writing extended state information... Done 
Building tag database... Done             
The following packages are BROKEN: 
  network-manager-gnome 
The following packages will be REMOVED: 
  network-manager 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 680kB will be freed. 
The following packages have unmet dependencies: 
  network-manager-gnome: Depends: network-manager (>= 0.6.5) but it is not installable 
Resolving dependencies... 
The following actions will resolve these dependencies: 

Remove the following packages: 
network-manager-gnome 
ubuntu-desktop 

Score is 188 

Accept this solution? [Y/n/q/?] y 
The following packages will be automatically REMOVED: 
  network-manager-gnome ubuntu-desktop 
The following packages will be REMOVED: 
  network-manager network-manager-gnome ubuntu-desktop 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 2519kB will be freed. 
Do you want to continue? [Y/n/?] 

Whatever all that means...

By the way, you have a gorgeous baby :)

---

### Post by TeoBigusGeekus on 2008-02-23
Cheers, she' s my niece!!
About UBUNTU:
Type y and install WICD.

---

### Post by Happibun on 2008-02-23
Typed Y

Got this -

bash: Y: command not found

:(

---

### Post by TeoBigusGeekus on 2008-02-23
Capital y (Y) perhaps?
What I mean is that you should accept the prompt's solution and then proceed with the installation. 
If you've already done so, just double click the .deb file....

---

### Post by Happibun on 2008-02-23
OK.

I think that I'd timed out the first time I tried, because it worked fine the second time I went from the Terminal command line.

I'm going to see if I can get online now. Back soon :)

---

### Post by Happibun on 2008-02-23
Right oh.

I think it is installed ok.

I went to the FAQ on the pages and followed this instruction to get the tray icon to appear -

* In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the “Startup Programs” tab, click the “New” button. Give it a name (”Wicd” works fine). For a command, enter “/opt/wicd/tray-edgy.py”.

...and I rebooted.

Only icon didn't appear and the machine is not online. 

I'm sorry, I must seem really thick. There is probably something really simple that I'm missing.

Jo

---

### Post by TeoBigusGeekus on 2008-02-23
Go to applications->internet->wicd to launch it.

---

### Post by Happibun on 2008-02-23
You'll be pleased to hear that I'm typing to you from the Linux machine.

I'm online through Wicd. I'll need to play about a bit to get the tray icon to load with bootup, but I already can see that I'm going to get on with this a lot better than Network Manager.

Thank you so much.

How do you go about thanking someone properly on these forums?

Jo

---

### Post by TeoBigusGeekus on 2008-02-23
The tray icon could be fixed by your next reboot. Have fun surfing!!!!

....to serve and to connect....

---

### Post by bopomofo on 2008-03-05
> **TeoBigusGeekus said:**
> I am not a wireless expert either but if you do a search (top right) in the Ubuntu forums you will find a lot of people complaining about Ubuntu wireless compatibility.
Now, my piece of advice:
Try to install an alternative network manager, namely WICD
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")
Since the time I replaced gnome-network manager with WICD I have noticed that my system runs more smoothly. Plus, I' ve read in some threads that a lot of people's wireless problems were solved using WICD.
Best luck!


This was great advice. I had been unable to connect to a WEP-protected wireless router through the Gnome Network Manager (WPA was fiine.

WICD worked for me. I'm on an ASUS U6 laptop with Gutsy.


As others have noted, using the WEP (hex) option appears to work.

---

### Post by CasPol on 2008-03-05
Hi there;

I have a laptop with a Broadcom wireless carda as well, and boy did I have some problems to get that up and running !!! Untill someone told me to do the following... ( it might take a little while so find your daughter somthing to do).

Connect your laptop to your wireless router with an ethernet cable. Start up and boot from the Ubuntu dvd and install Ubuntu all over again. When prompted at the end of the install remove the Ubuntu disk and restart but leave the ethernet cable connected. After the restart Ubuntu will look online for restricted drivers and will ask to permission to download them. This will include the driver for your broadcom card.
The driver will be downoaded, you can then complete the setings with the network manager and you should be good to go.

If you get an error message asking for the source, you need to ad some repositries, which is not difficult. Let me know how you get on...believe me it will work...I have been there ...

---

### Post by handydan918 on 2008-03-13
> I would prefer to hide my SSID and I really want to keep the MAC filtering on. I'm not too bothered about WPA, the way I see it - MAC filtering is the most secure way to protect my network. I would like the laptop to be able to connect to my network when it boots, without me having to jigger about with he router or terminal each time I want to connect.

Good that you got the bcm thing working. Those chips are a PITA!

Just wanted to clear up a misconception about mac filtering. 
It's not very secure.It takes very little time (seconds or maybe minutes) to use a packet sniffer and discern the mac address that is in use, spoof it, and gain access to the net work (and launch man-in-the-middle attacks...)
That said, I use it, too. It keeps the honest people honest, And I just don't do any kind of critical data transfers wirelessly.

---

### Post by anemptygun on 2008-04-03
Does anyone know if WICD is in the repositories, or if I can add it?

[edit]

this is the sources line for gutsy.
```

deb http://apt.wicd.net gutsy extras

```

[/edit]

---

### Post by anemptygun on 2008-04-04
> **Happibun said:**
> 
...and I rebooted.

Only icon didn't appear and the machine is not online. 

I'm sorry, I must seem really thick. There is probably something really simple that I'm missing.

Jo

They were doing this for edgy. In yours it's probably just tray-gutsy.py (or just tray.py this is what it is on my hardy install).

*In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the “Startup Programs” tab, click the “New” button. Give it a name (”Wicd” works fine). For a command, enter “/opt/wicd/tray-gutsy.py”.*

---

