---
title: "Help Please"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-11-21
:confused: I have just installed ubuntu linux and everything seemed fine until I tried to install my drivers. The cd -rom/dvd is not playing dvd's nor is it installing from product cd's when I put them in(such as dvd drivers, nvida Geforce fx 5200 software or modem software, etc etc.) When I try to connect it say server not found and when I check to see if my ethernet modem is installed it says modem not detected and the same for my dvd player. Why wont the auto play and install work with this linux. EVerything worked when I had windows xp os installed. Can anyone help please?????

Tribe One](*,)

---

### Post by Gaweph on 2006-11-21
for starters, was the internet working before you trtied to install the drivers for everything you mentioned.

If those drivers are made for windows they will not work.

For example the nvidia driver can be found by simply going to synaptic and searching for nvidia.

Check if the drivers are actually for linux (or they obviously wont work)

---

### Post by turbojugend_gr on 2006-11-21
HEHE m8, it's linux, you don't have to install drivers for your hardware. Your hardware should be recognized by default, exept for the nvidia card, read [this]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html") through about everything a new user would like to know. Welcome to UBUNTU.

Cheers, TJ.

---

### Post by Gaweph on 2006-11-21
Yes i think he has just put the cd into the drive (the cd that comes with windows drivers for his hardware)

As long as your modem is working (and it probably is working - so you have the internet.  you can then get anything you want by going to:

System>Administration>Synaptic Package Manager

Just do a search for what you want. then click Install, and away you go.

GoodLuck

---

### Post by tribeone on 2006-11-21
GAWEPH everything did work before I installed ubuntu. The guy that built my pc told me that linux would work on it if I wanted to install it.The cd rom/dvd player plays music cd's and I can open cd's to explore them. When I hook up the cable modem to the pc the light shows that there is a connection (pc activity) but linux says no connection detected. When I pu tin a dvd it says no uri handler.
  TJ thank you and I am glad to be free. Can't wait to get this thing running.

---

### Post by LLRNR on 2006-11-21
Hi and welcome!

To get started, check out [this guide](http://psychocats.net/ubuntu), it will answer many of your questions.

I never stumbled across network issues, so I'll have to leave this one out.

Regarding media content: DVDs and MP3 are restricted formats, since MP3 is a proprietary format and it's illegal to include full support on a standard install CD. Also DVDs stand under the international copyright issues... or something like this.

You WILL BE ABLE to play CDs and DVDs just as in Windows. You even have 2 ways:
- the easy way: [www.getautomatix.com](www.getautomatix.com) - this is an app that will install everything you need, just download and install it and tell it what you need ;
- the "other" way (I can't call it hard... it just another way) is [this](https://help.ubuntu.com/community/RestrictedFormats).

Regarding any other install issues, try [this guide](http://monkeyblog.org/ubuntu/installing/).

Your CDs with drivers won't word... they were designed for Windows in the first place... [This](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Graphics_Driver_.28NVIDIA.29) is for installing nVidia drivers, for instance.

Oh, there are much more to say... but get these done and if you need help, just ask !

Yes you're right, Linux IS [different](http://linux.oneandoneis2.org/LNW.htm) than Windows, but... give it a fair & honest try, ok ? ;)

Cheers!

LLRNR

---

### Post by tribeone on 2006-11-21
I pretty much figured I would be able to download what I needed from the internet. I usually do it that way (don't know why just do). All I need is to find away to get online ( linux can't see my modem). Once I get connect I am sure all will fall into place. Thanks so much you guy's for your help I will try what you have sugested and hope it works.

---

### Post by Ajd on 2006-11-21
Have you restarted your computer? Sometimes, on Linux especially, the best cure to a problem is restarting the computer.

---

### Post by tribeone on 2006-11-21
Ok, I used (sudo apt-get install nvidia-glx nvidia-kernel-common) in terminal and it came back nvidia kernel common is already the newest version. Then at the bottom says failed to fetch [COLOR="Blue"]http:/security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb temporary failure[/COLOR]. Then it says maybe run apt-get update or try with --fix-mis sing.

Don't I have to have a internet connection for that?

---

### Post by tribeone on 2006-11-21
> **Ajd said:**
> Have you restarted your computer? Sometimes, on Linux especially, the best cure to a problem is restarting the computer.



   Yes I did restart pc.  Still dosen't detect modem. The internet is there I am using it now on my laptop.

---

### Post by tribeone on 2006-11-21
ARRGGGHHH, I am goingnuts. LLRNR I followed the instructions in the dapper guide to identify modem chipset and it comes back no such file or directory. Why is my modem not detected? HELLPPP

---

### Post by LLRNR on 2006-11-21
Tribeone, I'm sorry, I told you in the beginning of my post I'm no good when it comes to networking devices. The link in the Dapper Guide I pointed was intended for your graphics card driver...

It is true that below there is a guide for installing a modem or something like this. In order for it to work, you DO need internet access : the two instructions starting with **wget** require that you already have internet access... 

I don't know what to say about modems, I never had one. I tried to give you a few hints on what I could and hopefully there will be somebody else around that will walk you through your modem issue.

LLRNR

---

### Post by tribeone on 2006-11-21
Thanks buddy. The info u gave me was very informative and will be a great help once I get connected. I forgot u did say u didnt know much about networking sorry.

---

### Post by LLRNR on 2006-11-21
That's ok, Tribeone, I'm sorry I can't help you any further. 

But since this is a stressing situation you're in, you definetely need your net up-and-running, I'd suggest you to go to your first post, click the symbol for Editing it (scissors I think), then as the textbox appears around your post click "Go advanced" and rename the title of your thread to something more suggestive, so that people who know how to deal with stubborn modems can help you easier... 

You could try something like "Can't install modem - UNSOLVED" or something like this. ;)

LLRNR

---

### Post by tribeone on 2006-11-21
Thanks LLRNR, i was thinking of changing the post title to something more specific. Will do.

---

### Post by tribeone on 2006-11-21
Just installed unbuntu linux 6.06 and it doesn't detected my eternet card/modem. Need help fast.

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> Just installed unbuntu and not detected by linux. Need help fast.

Linux doesn't detect Ubuntu? Huh? Ubuntu *is* Linux. Please give some more details so someone can help you.

---

### Post by seshomaru samma on 2006-11-22
Your post is not so clear
what is not ditected by Linux?
Which version of Ubuntu did you install
Did you get any errors when you installed
Can you describe what happens when you turn the computer on?
We would love to help you but we need more information

---

### Post by tribeone on 2006-11-22
Ubuntu linux 6.06 does not detect my ethernet card. When I run ifconfig -a in terminal I don't see eth0 or anything related to eth also when I run route in terminal I get back nothing under (destination, gateway, genmask Flags Metric Ref, Use Iface)

---

### Post by IYY on 2006-11-22
What sort of ethernet card do you have? Is it wireless? Is it a dialup modem? What does 'ifconfig' print out (just copy it here).

---

### Post by mssever on 2006-11-22
You're using a cable modem? How is it connected to your computer? My cable modem can connect via either USB or ethernet. If you use USB, you have to have drivers (and I seriously doubt that there are Linux drivers for your cable modem). If you connect via the ethernet port, you don't need drivers.

Look in /etc/network/interfaces (gksudo gedit /etc/network/interfaces) and make sure that the eth0 line (eth0 is the first--or only--network card on your computer) contains "dhcp". Here's mine:
```
auto eth0
iface eth0 inet dhcp
```Then, restart eth0: ```
sudo ifdown eth0; sudo ifup eth0
```Or reboot if that's easier for you.

Type ifconfig to see what kind of network info your system has.

---

### Post by tribeone on 2006-11-22
I am not on my linux pc this is my win xp laptop. I am unable to connect to the internet bacause the internal modem/ethernet card is not detected. external cable modem is working just fine. Even get light showing it is connected to pc when I connect  it to the linux pc.

The ifconfig -a shows only
lo  Link encap info and sit0 info just like evryone elses I have seen. It doesnt show anything for eth0.

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> I am not on my linux pc this is my win xp laptop. I am unable to connect to the internet bacause the internal modem/ethernet card is not detected. external cable modem is working just fine. Even get light showing it is connected to pc when I connect  it to the linux pc.

The ifconfig -a shows only
lo  Link encap info and sit0 info just like evryone elses I have seen. It doesnt show anything for eth0.

Try ```
sudo ifup eth0
``` and tell us what you get.

---

### Post by tribeone on 2006-11-22
> **mssever said:**
> You're using a cable modem? How is it connected to your computer? My cable modem can connect via either USB or ethernet. If you use USB, you have to have drivers (and I seriously doubt that there are Linux drivers for your cable modem). If you connect via the ethernet port, you don't need drivers.

Look in /etc/network/interfaces (gksudo gedit /etc/network/interfaces) and make sure that the eth0 line (eth0 is the first--or only--network card on your computer) contains "dhcp". Here's mine:
```
auto eth0
iface eth0 inet dhcp
```Then, restart eth0: ```
sudo ifdown eth0; sudo ifup eth0
```Or reboot if that's easier for you.

Type ifconfig to see what kind of network info your system has.
gksudo gedit /etc/network/interfaces says:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

but on the terminal window it says
(gedit:5304): GnomeUI- warning **: while connecting to session manager: Authentication Rejected, reason: None of the protocols specified are supported and host-based authentication failed

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> gksudo gedit /etc/network/interfaces says:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

but on the terminal window it says
(gedit:5304): GnomeUI- warning **: while connecting to session manager: Authentication Rejected, reason: None of the protocols specified are supported and host-based authentication failed
Everything looks OK. The GnomeUI warning is nothing to worry about--and totally unrelated to networking.

Have you tried ```
sudo ifdown eth0; sudo ifup eth0
```

Please post the results of that command.

---

### Post by tribeone on 2006-11-22
no not yet. So what your saying is that linux does detect my ethernet card?

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> no not yet. So what your saying is that linux does detect my ethernet card?

Probably. I've never had a network card that didn't work in Linux. The command I gave you should help to answer that question. If everything is normal, you should have Internet access after entering that command. If not, the error message(s) you get will help to diagnose the problem.

BTW: We're not talking about wireless, right?

---

### Post by tribeone on 2006-11-22
sudo ifdown eth0; sudo ifup eth0 gives me:
 
ifdown: interface eth0 not configured
Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet Systems Consortium.

SIOCSIFADDER: No such device
eth0: error while getting interface flags: no such device
eth0: error while getting interface flags: no such device
Bind socket to interface: no such device 
Failed to bring up eth0

---

### Post by tribeone on 2006-11-22
> **mssever said:**
> Probably. I've never had a network card that didn't work in Linux. The command I gave you should help to answer that question. If everything is normal, you should have Internet access after entering that command. If not, the error message(s) you get will help to diagnose the problem.

BTW: We're not talking about wireless, right?
yes your right not wireless

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> sudo ifdown eth0; sudo ifup eth0 gives me:
 
ifdown: interface eth0 not configured
Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet Systems Consortium.

SIOCSIFADDER: No such device
eth0: error while getting interface flags: no such device
eth0: error while getting interface flags: no such device
Bind socket to interface: no such device 
Failed to bring up eth0

Hmm...So there isn't an eth0 on your system it appears. Try ```
sudo lshw -class network
``` which will list all the network cards your system sees. If your card isn't there, you must have some unusual hardware. If it is, find the name given on the "logical name" line and use that in place of eth0.

---

### Post by tribeone on 2006-11-22
that command keeps taking me back to the command line.

---

### Post by tribeone on 2006-11-22
I just looked in my device manager and I see all my other hardware except my ethernet card, hummmm. I know it is there was connected when I had win xp installed, I also plug into it with the ethernet cable. the ethernet card is intergrated with the MB.

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> that command keeps taking me back to the command line.

You mean you don't see any output? In that case, do ```
sudo -v && sudo lshw | less
``` and manually look for your network card. If you don't find it, then you're right that Linux doesn't see your card.

In that case, what kind of card is it? How old? You might have to Google for info about getting it to work in Linux (using your card make and model). You can also try posting a separate thread about your network card (with a descriptive subject line) to see if anyone here knows about that card. As I said before, net cards have always worked for me out of the box, so I don't really know how to get the card recognized. I would be willing to help you interpret what you find if it's too advanced, though.

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> I just looked in my device manager and I see all my other hardware except my ethernet card, hummmm. I know it is there was connected when I had win xp installed, I also plug into it with the ethernet cable. the ethernet card is intergrated with the MB.

Hmm... What kind of mobo?

---

### Post by tribeone on 2006-11-22
I used that command and all the info about my MB is there. The mother board is an ecs elitegroup k7vta3 v8.0, 

core
product:kt333cf-8235 
vendor: via technologies 
physical id:0, 
slot: FDD, 

firmware
BIOS,
vendor: phoenix technologies,ltd,
physical id:0

Here's a link to se it
[COLOR="Blue"]http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=24&LanID=9&DetailID=352&DetailName=Specification[/COLOR]

---

### Post by tribeone on 2006-11-22
CPU    Socket 462 for AMD Athlon&#8482; XP/ Sempron&#8482;/ Athlon&#8482;/ Duron&#8482; processor 
 
  FSB 333/266/200 MHz 
 
 
CHIPSET    VIA® KT333CF & VT8235 
 
  North Bridge: VIA® KT333CF 
 
  South Bridge: VIA® VT8235 
 
 
 
LAN    VIA® VT6103 10/100 Mbps Fast Ethernet PHY

---

### Post by karamba_kid on 2006-11-22
> **Ajd said:**
> Have you restarted your computer? Sometimes, on Linux especially, the best cure to a problem is restarting the computer.

I would have to disagree on that point.  Most services (servers, networking, etc.) in linux can be restarted manually.  This is because configurations is kept in nice readable text files and not this one huge ugly binary registry like in windows.

---

### Post by tribeone on 2006-11-22
Guy's this is my ethernet card [COLOR="blue"]http://www.vntek.com/en/products/tahoe/vt6103/[/COLOR]. 

It is intergrated on my MB which is this:
[COLOR="Blue"]http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=24&LanID=9&DetailID=352 &DetailName=Specification[/COLOR]

---

### Post by pengo on 2006-11-22
Blank post. Sorry can't delete it. Mods do it if you like(can't find the option)

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> Guy's this is my ethernet card [COLOR=blue]http://www.vntek.com/en/products/tahoe/vt6103/[/COLOR]. 

It is intergrated on my MB which is this:
[COLOR=Blue]http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=24&LanID=9&DetailID=352 &DetailName=Specification[/COLOR]

Are you using an AMD64 machine? I found this, which might help: [http://mike.kruckenberg.com/archives/2005/01/amd64_gentoo_li.html](http://mike.kruckenberg.com/archives/2005/01/amd64_gentoo_li.html)

To adjust for Ubuntu, do ```
sudo modprobe via-rhine
```

Then, re-do the lshw stuff and see if your net card shows up.

---

### Post by mssever on 2006-11-22
> **pengo said:**
> Hello everyone:p I'm a newbie both in the forum and in linux. I installed the ubuntu 6.06 a couple of weeks ago in my computer but I have problem connecting to the internet. I use a Netgear WG511T wireless card which supports the WPA-PSK security. Ubuntu doesn't have problem recognizing the card but as you know the WPA has to be manually set up. I tried to follow the instructions from the ubuntu wiki-here: 
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
but they seem to be a little complicated for me(n00b:sad: ).
I also tried following instructions from here also:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
Anyway I have a bunch of questions: first of all I can't install(with or without the ubuntu CD) the network-manager-gnome package. Says it can't locate it. What's wrong? In several points in the tutorials says create a file. How do I do that? Using the graphical interface for /etc catalog appears a message that I don't have the rights to do that. I know sudo -s but it does work only in Terminal(and I don't know how to create files from terminal). And what does it mean to comment out something? Just place a # in the beginning? 
Apart from these is there a package to do the job(even unofficial) and not having to create everything manually?
Thanks in advance, sorry for the big post, and pleeeeeeeeeease heeeeeeeeeeeeeeeelp:cry:

/edit: I know it's off-topic , thought the thread was for general help. Mods if you find it necessary move it in the appropriate thread where I can find help easier. Sorry(can't delete it why?)

You might be better off just starting a new thread. You can edit this one and blank it if you wish.

---

### Post by tribeone on 2006-11-22
No I am using amd atholon xp 2500+ barton core. I will still check that link out.

---

### Post by tribeone on 2006-11-22
Ok i went ahead and bought a new ethernet card. I have the d-link 530tx+. Now linux detects my card and it is there but still can't get online.

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> Ok i went ahead and bought a new ethernet card. I have the d-link 530tx+. Now linux detects my card and it is there but still can't get online.

Can you go through the previous troubleshooting steps again for me, especially the ifdown and ifup parts.

---

### Post by tribeone on 2006-11-22
You mean before the new eth card?

---

### Post by mssever on 2006-11-22
> **tribeone said:**
> You mean before the new eth card?

With the new card, if you still can't get online. You might have to do sudo lshw -class network to find the proper name to use.

---

### Post by tribeone on 2006-11-23
That issue was resolved. I just had to reset my cable modem and resart pc.

---

### Post by tribeone on 2006-11-23
Now I am trying to get my cd-rw/dvd-rom player to play. It will play music but not dvd's

---

### Post by mssever on 2006-11-23
> **tribeone said:**
> Now I am trying to get my cd-rw/dvd-rom player to play. It will play music but not dvd's

You need libdvdcss2. See this link: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by tribeone on 2006-11-24
Thanks for all your help guys mssever you have been a big help. I am finally up and running (I think). Just a few more tweeks and good to go. Now I am trying to get my usb and printer to work. USB is not working.

---

### Post by mssever on 2006-11-24
Open up a terminal and type ```
less /var/log/messages
``` then hit <shift>+F. Now, plug in your printer and watch what messages appear. If USB isn't working at all, you probably won't see anything related to USB. If you get USB stuff, post it here. Otherwise, the problem is likely your printer. What kind of printer is it?

---

### Post by tribeone on 2006-11-24
OK, I don't know but this is what returned:

ly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 24 23:04:05 Tribeone gconfd (ummalharith-8046): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 24 23:04:07 Tribeone gconfd (ummalharith-8046): Resolved address "xml:readwrite:/home/ummalharith/.gconf" to a writable configuration source at position 0
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): starting (version 2.14.0), pid 8473 user 'abu-harith'
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readwrite:/home/abu-harith/.gconf" to a writable configuration source at position 1
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 24 23:09:25 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readwrite:/home/abu-harith/.gconf" to a writable configuration source at position 0
Waiting for data... (interrupt to abort)


abu-harith@Tribeone:~$ ly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
> Nov 24 23:04:05 Tribeone gconfd (ummalharith-8046): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
> Nov 24 23:04:07 Tribeone gconfd (ummalharith-8046): Resolved address "xml:readwrite:/home/ummalharith/.gconf" to a writable configuration source at position 0> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): starting (version 2.14.0), pid 8473 user 'abu-harith'
> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readwrite:/home/abu-harith/.gconf" to a writable configuration source at position 1
> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
> Nov 24 23:09:24 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
> Nov 24 23:09:25 Tribeone gconfd (abu-harith-8473): Resolved address "xml:readwrite:/home/abu-harith/.gconf" to a writable configuration source at position 0
> Waiting for data... (interrupt to abort)

---

### Post by mssever on 2006-11-26
Hmmm... Let's see if the system sees your USB ports and such. ```
sudo lshw | less
``` Look for USB stuff. You might try plugging in random USB devices to different ports to see if those devices show up, as well.

If you don't see usb stuff, then your system doesn't see your USB ports. You should probably start a separate thread about that, as I have no idea how to make USB work. It always Just Works for me.

If you do see USB stuff, but not your printer, look for your printer on [http://linuxprinting.org](http://linuxprinting.org) and see what that site has to say about its Linux compatibility. If your printer has a parallel port interface, you might try that, as well.

---

### Post by tribeone on 2006-11-27
What does this mean? This is what returned with the sudo lshw | less command

tribeone
    description: Desktop Computer
    product: KT333CF-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: KT333CF-8235
       physical id: 0
       slot: FDD
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/22/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot

---

### Post by mssever on 2006-11-27
> **tribeone said:**
> What does this mean? This is what returned with the sudo lshw | less command

tribeone
    description: Desktop Computer
    product: KT333CF-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: KT333CF-8235
       physical id: 0
       slot: FDD
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/22/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot

This is a description of your motherboard and BIOS. Notice the description lines.

BTW, if you paste files and the results of commands in code blocks (the # sign on the toolbar), then it will preserve indentation and turn off word wrapping. This makes a lot of stuff much easier to understand.

---

### Post by tribeone on 2006-11-27
So according to this it is reading my usb? It says (usb agp ls120boot zipboot)```

```

---

### Post by mssever on 2006-11-27
Those are your motherboard's capabilities. You should have a whole section for USB. Here's the USB portion of what I get from that command, for reference: ```
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@00:0b.0
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:2000-201f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b.1
             bus info: pci@00:0b.1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:2020-203f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: Logitech USB Keyboard
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 15.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: b.2
             bus info: pci@00:0b.2
             version: 51
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d0005000-d00050ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-686 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
```

---

### Post by tribeone on 2006-11-27
YAHHOOOOOOO!!!  I went into BIOS and found that my usb and onboard modem was not enabled they were both disabled. All I had to do was enable them restart pc and viola now I get this

```
~$ lshw
WARNING: you should run this program as super-user.
tribeone
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: d0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:e0000000-e0ffffff iomemory:d8000000-dfffffff irq:11
        *-network:0
             description: Ethernet interface
             product: VT6105 [Rhine-III]
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 86
             serial: 00:17:9a:ba:d5:3d
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine ip=192.168.0.101 multicast=yes
             resources: ioport:d000-d0ff iomemory:e2010000-e20100ff irq:10
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Camera
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=quickcam maxpower=500mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:5
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e2011000-e20110ff irq:3
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e000-e00f irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: MDT MD800AB-22CBA1
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SONY CD-RW CRX300E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:e400-e4ff irq:5
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth1
             version: 74
             serial: 00:0d:87:56:8d:32
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine multicast=yes
             resources: ioport:ec00-ecff iomemory:e2012000-e20120ff irq:11

and this
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:9A:BA:D5:3D
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:feba:d53d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54832 (53.5 KiB)  TX bytes:6075 (5.9 KiB)
          Interrupt:10 Base address:0xd000

eth1      Link encap:Ethernet  HWaddr 00:0D:87:56:8D:32
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
 I can't believe it was such a simple thing. Thanks so much guy's.
```

---

### Post by mssever on 2006-11-27
Great! I noticed that your camera was detected. Do you have your printer working, now?

---

### Post by tribeone on 2006-11-27
no the printer is not printing don't know why.Can't figure out how to use the webcam either.

---

### Post by mssever on 2006-11-27
> **tribeone said:**
> no the printer is not printing don't know why.Can't figure out how to use the webcam either.

OK. I don't know anything about getting webcams working, but now that USB is up, we should be able to make progress with the printer.

First, what kind of printer do you have (make/model)? Have you gone through the add printer routine? If so, what was the result (including any error messages)?

Next, look at lshw again with the printer plugged in. You should see it listed with the USB stuff.

---

### Post by tribeone on 2006-11-27
I have a lexmark x1150. I ran the add printer and it loaded a driver from the  linuxprinting.org site. When I ran a test page print out it returned stopped:job stopped. In admin-printer it shows 5 jobs ready to print but all 5 jobs say stopped:job stopped. The printer shows up everywhere from the command line. seems weird to me. The lshw command returns this:

    ```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: d0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:e0000000-e0ffffff iomemory:d8000000-dfffffff irq:11
        *-network:0
             description: Ethernet interface
             product: VT6105 [Rhine-III]
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 86
             serial: 00:17:9a:ba:d5:3d
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine ip=192.168.0.101 multicast=yes
             resources: ioport:d000-d0ff iomemory:e2010000-e20100ff irq:10
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Generic USB device
                   product: Camera
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=quickcam maxpower=500mA speed=12.0MB/s
              *-usb:1
                   description: USB hub
                   product: USB Hub
                   vendor: Lexmark
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=8mA slots=2 speed=12.0MB/s                 *-usb:0 UNCLAIMED
                      description: Generic USB device
                      product: X1100 Series
                      vendor: Lexmark
                      physical id: 1
                      bus info: usb@2:2.1
                      version: 1.00
                      serial: 0664344
                      capabilities: usb-1.10
                      configuration: maxpower=0mA speed=12.0MB/s
                 *-usb:1
                      description: Printer
                      product: Lexmark X1100 Series
                      vendor: Lexmark
                      physical id: 2
                      bus info: usb@2:2.2
                      version: 1.00
                      serial: 0664344
                      capabilities: usb-1.10 bidirectional
                      configuration: driver=usblp maxpower=4mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:5
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e2011000-e20110ff irq:3
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e000-e00f irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: MDT MD800AB-22CBA1
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SONY CD-RW CRX300E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:e400-e4ff irq:5
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth1
             version: 74
             serial: 00:0d:87:56:8d:32
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine multicast=yes
             resources: ioport:ec00-ecff iomemory:e2012000-e20120ff irq:1
```1

---

### Post by mssever on 2006-11-27
Unfortunately, you seem to have been bitten by the Lexmark bug. Lexmark printers are famous for their incompatibility with Linux (they're the worst), and many don't work at all. According to [this page]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-x1150_PrintTrio"), yours has earned a rating of "paperweight"--in other words, the best Linux minds can't get the thing to work.

The problem is that Lexmark uses a proprietary driver system that actually does a lot of the firmware work in the driver--which saves them money. Unfortunately, this also makes their drivers extremely difficult to reverse engineer, and Lexmark has been less than cooperative in the process.

Plus, those of us who are experienced in Linux know not to buy a Lexmark, so it isn't very likely that someone will put serious effort into reverse engineering your printer.

---

### Post by tribeone on 2006-11-28
how do I delete the driver I loaded for it?

---

### Post by mssever on 2006-11-28
Did you manually install a driver, or did you use the one that the add printer applet recommended? If it was the default driver, just delete the printer. If you downloaded the driver, it depends on the driver as to how you uninstall it. AFAIK thare really isn't a standard way of doing it. It's likely that there are one or more directories with the driver name--rename them, and if you don't have any problems after a while, delete them.

BTW: In case you're in the market for a new printer, HPs are probably the best supported. HP actually releases open source Linux drivers for their printers. Mine works without a hitch.

---

### Post by tribeone on 2006-11-28
I used the one in add printer. I just deleted the printer and pulled the usb cable.Thanks for the advice I will look into the hp printers. I do have  two of them already being used with the other two pc's.

---

### Post by mssever on 2006-11-28
> **tribeone said:**
> I used the one in add printer. I just deleted the printer and pulled the usb cable.Thanks for the advice I will look into the hp printers. I do have  two of them already being used with the other two pc's.

Oh, one more thing. Before you buy a printer, look it up on linuxprinting.org...just to be safe.

---

### Post by apral on 2006-11-28
I had to enter my isp's dns & static ip address manually in system-network                   (a phone call to them will get the info).Try this.Best of luck.:)

---

