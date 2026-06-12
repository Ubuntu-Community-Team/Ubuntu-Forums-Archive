---
title: "Linksys USB Network Adapter not being seen"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mynameisbill on 2007-06-13
I have a Linksys Wireless USB Network Adapter (Model No, WUSB54G) When I load up Ubuntu, it doesn't detect a wireless device. I tried iwconfig, but it just had lo and eth0 as "no wireless extentions" I checked the list of wireless cards and it appears that the adapter I have is supported. Any help would be greatly appreciated :p

---

### Post by xMave on 2007-06-13
Seems like many of us are having this problem, what version? I'm using v4, if you find anything, be sure to tell me and I'll do the same ;)

---

### Post by Bachstelze on 2007-06-13
You guys most likely just need to install ndiswrapper :)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by xMave on 2007-06-13
Easier said than done :(

---

### Post by mynameisbill on 2007-06-13
I tried installing ndiswrapper, but when I attempted to it gave me all kinds of errors and warnings.

---

### Post by Bachstelze on 2007-06-13
Sorry, my crystal ball is currently under maintenance so please provide more info about the errors you get if you want me to help you ;)

---

### Post by mynameisbill on 2007-06-13
Okay, I have ndiswrapper installed, but there's still no wireless connection under iwconfig or under Administration - Network.

I see a lot of other people are having issues with this. Anyone know any other methods I could try?

---

### Post by Bachstelze on 2007-06-13
Check if ndiswrapper is properly installed :

```
ndiswrapper -l
```

should report "driver installed, hardware present".

---

### Post by mynameisbill on 2007-06-13
It just has the driver name and driver installed, doesn't say anything about the hardware.

---

### Post by Bachstelze on 2007-06-14
Then, it means you installed the wrong driver. Please run

```
lsusb
```

and paste what you get (or at least the line about your wireless thingie).

---

### Post by mynameisbill on 2007-06-14
There's only 2 that come up with anything

Bus 004 Device 002: ID 1915:2234
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp.

The rest are all ID 0000:0000

---

### Post by Bachstelze on 2007-06-14
Try this driver

[http://www.sitecom.com/showdownload.php?id=1998](http://www.sitecom.com/showdownload.php?id=1998)

Someone reported success with it on the ndiswrapper wiki.

---

### Post by mynameisbill on 2007-06-14
That worked perfectly, I can see all the wireless networks now. Thank you SO much for all your help!

---

### Post by NfF on 2007-06-14
You can get the build-essentials package from the ubuntu cd (if you choose). Place CD in drive. 
At command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Once this package is installed you can then re-enter into the directory structure where you unzipped/untarred the ndiswrapper source files. Then at command prompt
make distclean
make

If you get no errors (hopefully you wont - now install the package):
sudo make install

Check if it was installed properly:
ndiswrapper -v

A version number should print.

That is how you install ndiswrapper (well actually compile and install from source files!)

If you need more help with driver installation after this step let me know -- As of yet we havent done anything with your wireless card drivers. Ndiswrapper is a program that "wraps itself" around windows drivers making them appear like linux drivers to the operating system. The next step is to find the correct version of the card drivers compatible with the card and ndiswrapper, then "wrap" the driver, install the "ndiswrapper-driver" combination, make a few configuration file changes, reboot computer, and then enjoy!!!

---

### Post by Evan394 on 2007-06-15
Ok Hymn, I'll bite (I have the identical Linksys device mentioned above, and have ndiswrapper installed properly)

I did ```
lsusb
``` and got the following ```
Bus 002 Device 005: 13b1:001e Linksys
```

That's it so far.  I have not installed any driver, just ndiswrapper and plugged in the WUSBF54G.

What's next please.

---

### Post by Bachstelze on 2007-06-15
No need for ndiswrapper, native Linux drivers for your adapter exist. If you're running FEisty, try to do :

```
sudo modprobe zd1211rw
```

If it goes without errors, do

```
sudo iwconfig
```

and you should see your wireless interface.

---

### Post by Evan394 on 2007-06-15
Uh oh,

let me clarify somthing with you, Hymn.  in "zd1211rw" are those ones or letters?

I chose ones and after entering ```
sudo modprobe zd1211rw
``` nothing happened. (no errors, no output, nothing. Just another line with user@computer:~$).
then I tried ```
sudo iwconfig
``` and got:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.
```

---

### Post by peter_k on 2007-06-29
I am having a similar issue, so I've kind of been watching this thread too.

I am trying out edubuntu for my kids' Dell, and am running it off the LiveCD I made. Looks great, but my wireless is not working.  I have the aforementioned Linksys WUSB54G, v 4.3 (according to the install disk).  It is connecting to my downstairs PC that runs Feisty, and uses a Linksys WRT54GS router.

The Linksys device seems to be recognized as a USB device on the edubuntu box, as it comes up in Hardware manager.  In the Devices section of Network Tools, it comes up as "Unknown Interface (rausb0)", has an IP address of 
IPV6  fe80::216:b6ff:fe5a:9fcb, a netmask prefix of 64, and a Scope of "Link." 

I tried some of the commands from here, and got the following results:

lsusb:
-------
bus 004 device 002 ID 1361:000d Linksys

sudo modprobe zd1211rw returned no response, and took me back to the prompt.

sudo iwconfig:
------------------
no wireless connections at lo or eth0, just like Evan394.

at "rausb0" I get: 

RT2500 WLAN ESSID: "linksys" Nickname: ""
mode: managed Frequency: 2.437 GHz Access Point 00:14:BF:39:68:33
Bit Rate: 54 Mb/s  RTS Thr: off Fragment Thr: off Encryption key: off Link quality: 79/100
signal level -71 dbm Noise level: -212 dbm Rx invalid nwid:0 Rx invalid crypt: 0
Rx invalid frag:0 Tx excessive retries: 0 Invalid misc: 0 missed beacon: 0

Similar to what was listed above, but not the same.  Under Network, I see Wired and Wireless, and have tried all different combinations of roaming, DHCP, IPv4, but to no avail.

I feel like edubuntu is seeing it, but just can't use it (no sites come up in firefox).  I have read about ndiswrapper and madwifi, and that may work; however, as their is no wired connection on this box (it normally runs XP through the wireless adapter and connects fine), I can't download via synaptic to add ndiswrapper - could I download it to a CD from my feisty box and run it then?  My only concern with that approach is that I though I would have to do the actual install to do that, as the LiveCD would be in the drive already, and if it doesn't work, that might be rough.  I would guess the same scenario might apply to the driver HymnToLife mentions above. 

Any ideas?

Sorry for the long post, but I figured giving as much info as possible would help

---

### Post by peter_k on 2007-06-29
Interestingly enough, I burned a few .isos of various distros to see what would work...Knoppix didn't recognize the card, but Kanotix did - after I ran the config utility (I believe it was knemo) on the network card, and supplied only the ESS and frequency, and left everything else blank. (If somehow I could get these options in edubuntu, I think I'd be homefree - perhaps I should see if I can install knemo? ) Strange, since my understanding was that Kanotix is based on Knoppix.  I'm not letting the kids use it though, because:

1. Kanotix seems pretty powerful in terms of what it supplies as far as programs.  Just powerful enough for my kids to muck it up. :)

2. I do like the fact thatevidently you can use rpm's and deb's right out of the box.  I've kind of gotten used to the Ubuntu repos, though, so I couldn't find anything, but that might change with time.  Kanotix seems more like an adult distro though - plenty of programming and useful stuff, and no games except for Super Tux and Mahjongg.  I'd have to download plenty of programs to get it up to what edubuntu has.

3. I've heard too many stories about how Knoppix recognizes a card from the LiveCD, but then not on the HDD install; I might be wrong here, but as Kanotix is based on Knoppix, I wouldn't be surprised if that happened.

If someone is a programmer/power user, I'd guess I could recommend Kanotix to them, but I don't think it's kid-friendly, at least not for my kids who always seem to break stuff. :) 

All in all, I'd prefer to use edubuntu for my kids, provided I could get the wireless issue fixed.

---

### Post by usmanlinux on 2007-10-12
> **HymnToLife said:**
> Try this driver

[http://www.sitecom.com/showdownload.php?id=1998](http://www.sitecom.com/showdownload.php?id=1998)

Someone reported success with it on the ndiswrapper wiki.

I am working on a system for a friend, got him to convert over.. but i cant seem to get it working either.

ive got ndiswrapper installed. I can see it on bus 7, but cant seem to get it to show under "iwconfig"

ive followed all the steps. and unfortunately his video is screwy also, but i figured let me get the machine to see the internet and all those issues can be resolved.

please advise.

thanks.

---

