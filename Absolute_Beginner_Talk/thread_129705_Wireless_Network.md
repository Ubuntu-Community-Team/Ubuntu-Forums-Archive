---
title: "Wireless Network"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by depeche on 2006-02-14
Hello,

I entered sudo lshw -C network:

decription:  Ethernet interface
product:  SiS900 PCI Fact Ethernet
vendor:  SiS
physical id:  4
bus info:  pci@00:04.0
logical name:  eth0
version:  91 
serial:  00:c0:9f:97:b6:e6
size:  10MB/s
capacity:  100MB/s
width:  32 bits
clock:  33MHz

I then entered lspci -v:

Ethernet Controller:  SiS900 PCI Fast Ethernet (rev 91)
Subsystem:  Acer Incorporated:  Unkown device 0083
Flags:  bus master, medium devsel, latency 173, IRQ 19
I/O ports at 1800 [size=256]
Memory at e2005000 (32-bit, non prefetchable) [size=4k]
Capabilities:  <available only to root>

I next entered sudo modprobe sis900

then, sudo iwconfig:

lo:  no wireless extensions

sit0:  no wireless extensions

eth0:  no wireless extensions

I'm unsure of what to do next.  Any suggestion?

Thank you.

---

### Post by veniceanonymus on 2006-02-14
just a guess: are you trying a wireless connection? all info are pointing to a wired one...

---

### Post by bscbrit on 2006-02-14
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Yes, follow the guide in the link above.  ;)

---

### Post by veniceanonymus on 2006-02-14
I strongly advise you to follow the links posted by bscbrit. That's how I started learning... Good job bscbrit and thank you

---

### Post by depeche on 2006-02-14
veniceanonymous - it's definitely wireless, and I'm heading to bscbrit's link right now...

bscbrit - Thank you.  I'll give it a whirl.

---

### Post by TrendyDark on 2006-02-14
That link was for Wired Ethernet, but um. . . just use ndiswrapper to get your wireless interface up and running. You'll need to get the Windows XP drivers for it, but it's very simple to use, I use it at home.

---

### Post by depeche on 2006-02-14
trendydark - I'm completely new to linux and ubuntu.  Could you elaborate more on the ndiswrapper, or point me in the right direction?  Thanks.

---

### Post by TrendyDark on 2006-02-14
okay, ndiswrapper is a package used to install the windows drivers for wireless cards, which is the piece of hardware i'm assuming you're having trouble with. 

To install it, goto System> Administration> Synaptic, search for ndiswrapper (use the search button).

Mark to install, then hit apply.

Now open up your terminal and type: ndiswrapper -i path/to/the/windows/driver

then: modprobe ndiswrapper

that should do it, now all you're going to need to do is add ndiswrapper to the list of modules to boot on startup, use this command:

sudo gedit /etc/modules

---

### Post by bscbrit on 2006-02-14
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Apologies depeche - I hit the wrong link, but you already know that! :o

---

### Post by depeche on 2006-02-14
No problem, bscbrit.

I marked the ndiswrapper to install, then hit "apply."  A warning message popped up reading:  W:  failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb)
Temporary failure resolving 'archive.ubuntu.com'

I'm completely confused.  Why is it trying to fetch a url when the reason I'm installing ndiswrapper is because I can't connect to the network.

---

### Post by bscbrit on 2006-02-14
Disable all the repos other than the CD, at least until you get your connection working.

Yes, I know that its obvious to humans that you would need ndiswrapper to create your wireless connection, but that is taking computer intelligence just a little bit further than is practical at the moment.....:p

---

