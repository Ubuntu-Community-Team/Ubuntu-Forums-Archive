---
title: "Netgear WG111"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by tjpren on 2007-09-28
Hello, I've recently installed Ubuntu V7.04 as a dual boot (with Win XP).  I've decided to jump right in, and start getting my wireless connection setup.

I've read most of the threads, from previous posts, and done the google bit, but am none the wiser.

To date, I've installed the ndiswrapper (it seems to install OK, as I get an Icon for it in the system>>administrator drop down).

I've created a directory in my desktop, and added all the drivers from the WG111 CD.

When I try to do a :
sudo ndiswrapper -i ~/netgeardrivers/netwg111.inf
I get an error "couldn't open" etc.
I'm runniing now in XP, as I've closed down my Ubuntu OS, I can't reproduce the entire error- but it basically refers to INF file and directory I've created.

My suspicion is that its a directory permission thing.

Any ideas appreciated

Regards

---

### Post by SpiritIsReality on 2007-09-28
howdy

I've seen it mentioned in the ndiswrapper docs somewhere, that if it doesn't work, try the drivers
from ndiswrapper.org 
#10 or #11 here? I'll have to check.
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)
after ndiswrapper, then there's the WifiDocs here
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

trails.

---

### Post by SpiritIsReality on 2007-09-28
>3.4.2. Installing Windows driver using command line
heading here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)
if unsure. post back here, and we'll see what we can do.
trails

---

### Post by SpiritIsReality on 2007-09-28
this the guide you used?
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28111%29%7C%28wg%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28111%29%7C%28wg%29)
found this with this forums advanced search, keyword wg111...search titles only
[http://ubuntuforums.org/showthread.php?t=560296&highlight=wg111](http://ubuntuforums.org/showthread.php?t=560296&highlight=wg111)
[http://ubuntuforums.org/showthread.php?t=524284&highlight=wg111](http://ubuntuforums.org/showthread.php?t=524284&highlight=wg111)
[http://ubuntuforums.org/showthread.php?t=32929](http://ubuntuforums.org/showthread.php?t=32929)
worth a look?

---

### Post by tjpren on 2007-09-29
hello,
thanks for the feedback guys.  Unfortunately no luck so far.

I think the issue I originally posted was due to permissions, and my unfamiliarity with Ubuntu.

I read through the articles again, and tried ndiswrapper -i direct from the CD, and it appeared to install OK.  

However, using ndiswrapper -l, all I get is netwg111:driver installed.  No hardware is shown.

I've also downloaded a different driver set from netgear, as it appears as though my device is a V1 not V2.  Again, no luck.  Its as if it can't see the USB device.  Doing lsusb, I get no device, except for my optical mouse, and external HD.

I know the USB ports work, as in Windows, I'm using all three USB devices.

Anyhow, any thoughts gratefully accepted

Regards

---

### Post by tjpren on 2007-09-29
Guys,

Some more info-
I've been wondering whether the ndiswrapper is installed correctly - I seem to remember seeing more reference to it being a command line install, than using the synaptic manager.

Anyway, I've uninstalled it, and am trying to reinstall from command line, but am getting an error.

This is my command line, which shows that I have the ndiswrapper in several folders below my desktop.

administrator@scada-dev:~$ sudo dpkg -i /administrator/desktop/ndiswrapper/ndisfeisty/ndiswrapper-common_*.deb

This is my error:
dpkg: error processing /administrator/desktop/ndiswrapper/ndisfeisty/ndiswrapper-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /administrator/desktop/ndiswrapper/ndisfeisty/ndiswrapper-common_*.deb
administrator@scada-dev:~$ 

My thinking is a bit like at the start of the thread- my unfamiliarity with how Ubuntu sees folders.

Any help?

---

### Post by SpiritIsReality on 2007-09-29
howdy
sorry about the delay. it's 04:49 (am) here. Somebody could have probably helped you out.
but it seems like some guys don't want to butt in. I can see that in some instances, but you
can't do better than teamwork I recon. unless you let somebody have permission to do a remote
desktop assistance, you're still in the saddle, no one else drivin, but I guess it could get confusing
trying to figure out who to listen to. listening to them all, hammering at the terminal not knowing
what in sam hill's going on...
OK ...there's a space in the file name
> administrator@scada-dev:~$ sudo dpkg -i /administrator/desktop/ndiswrapper/ndisfeisty/ndis wrapper-common_*.debdo you see it?
and there should be a ~in front of the /administrator if the directory (folder) is in your /home
I don't have any experience with the hardware you're using for the wifi. I don't have any 
experience at wifi at all to speak of. I did get a linksys wp54 or something working on a 
toshiba satellite 2140 xcds by following the ndiswrapper docs (documentation) on the 
[http://help.ubuntu.com/community](http://help.ubuntu.com/community) site. searched for wifi and then searched for ndiswrapper.
OK
maybe just for the hell of it,what you could try is open a  terminal and run
```
sudo dpkg -i administrator/desktop/ndiswrapper/ndisfeisty/ndiswrapper-common_*.deb
```
that's one space between sudo and dpkg and -i and administr......no other spaces. 
if you know how to copy and paste the code into the terminal, you could do that. if you don't
know how to copy and paste and you ask, you will. you know what i'm tryin' to say? haha!

ok I better let you read this and see what you can do.
all the best
trails
buds

---

### Post by tjpren on 2007-10-01
Thanks to all responses.  I'm alive and connected to the internet with my WiFi now.  For those that come after, here is a summary of my steps.

**Copy to CD**

Download the ndiswrapper for your particular version of Ubuntu as described in
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
For 7.04 Feisty Fawn 
a.[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common) 
b.[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9) 
c.[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) 
Burn these files to a CD.

**Install Ndiswrapper**

sudo dpkg -i /media/cdrom/feisty/ndiswrapper-common_*.deb
sudo dpkg -i /media/cdrom/feisty/ndiswrapper-utils*.deb
sudo dpkg -i /media/cdrom/feisty/ndisgtk_*.deb

**Install Netgear INF file**

Install off the install CD that came with USB dongle, but use the ndis5 directory.

sudo ndiswrapper -i /media/cdrom/ndsi5/netwg111.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
[B]
Edit Blacklist[/B]

gksudo gedit /etc/modprobe.d/blacklist
[...add to the bottom of the listing....]
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb

gksudo gedit /etc/modules/

''...add to bottom of the listing...''
ndiswrapper


**Configure Network**

sudo gedit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wireless-essid <my ssid>
wireless-mods managed
[B]
Reboot[/B]
This was an important step, and one I that I continually overlooked.  Reboot, and only then, plug the USB dongle in place.
At this point the blue light came on the dongle, and I was able to start Firefox, and connect to my websites.
I also noted that running System>>Administration>Network now showed a wifi network connection.

I am still unfamiliar with Ubuntu permissions, so, experienced users will probably cringe at my burning downloads to CD, but I couod not honestly get an install from files stored within my desktop.

Anyway....thats my lot, again thanks to everyone, and to those who came before with their own personal stories ......thanks.
:)

---

### Post by SpiritIsReality on 2007-10-01
howdy
Good going! That was a rough ride!
About file permissions:
[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#gosnautilus-476](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#gosnautilus-476)
and there is the "Know Your Terminal Commands" ... library that omnios and all
have put together here. [http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507) .
from "Important Links" sticky in the Absolute Beginner's forum. linuxcommand.org is recommended
buds

---

### Post by jw5801 on 2007-10-01
I'll throw in my two cents at this stage, even though it's solved anyway! I have a Netgear WG111v2 wireless usb adaptor, and it worked out of the box (I use it to install the drivers I need for my internal card). I think the issue here is not having a driver for the wireless adaptor so much as getting Linux to recognise it as a device in the first place. Even if you had no driver for it whatsoever it would still appear in lsusb, even if it was just as "Unkown Device."

---

### Post by Craptron2000 on 2007-11-29
Hi, I'm a complete n00b but I've found a really easy GUI way using version 7.10 of Ubuntu. 

Step 1
With the WiFi card installed plugged into a USB port, go to the System menu --> Administration -->Synaptic Package Manger

Step 2
Click on Search, and type ndiswrapper

Step 3
Click on ndisgtk (graphical frontend for ndiswrapper) and follow the prompts to install the package (includes 3 items altogether). It will ask for the 7.10 CD and you will need wired internet access at this stage also

Step 4
Follow the prompts and it will ask you for the ".inf" file. Just insert the CD that came with your wifi adapter and it will automatically display the files. Drag the netwg111.inf file to the other window and click open

Step 5
Just follow the prompts and it will install the driver then take you to a small window called "Wireless Network Drivers". Click on "Configure Network" button, then select Wireless Connection and click on "Properties".

Step 6
Type in the details you set up in your router (SSID, authentication type, password) and you're ready to roll

Step 7
Unplug your cable and test

Cheers,
B.

---

### Post by Chouette on 2008-01-20
I don't know if anyone even watches this thread but hopefully someone can help me, I have the same adapter and I have tried everything one this thread but whenever I plug in the adapter the light comes on and my computer freezes completely, no mouse, no keyboard anything.  My mouse is on USB next to the adapter, if that matters.  Please help, any ideas as to why this is happening?

---

