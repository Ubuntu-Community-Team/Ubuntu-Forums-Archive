---
title: "First Day Ubuntu user - Wireless got me frustrated"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Airist on 2007-07-21
This is my first day using Ubuntu.  So far the install went well. However, the first thing I tried to do is connect to my router through my wireless card (D-Link DWL-520) and was not able to.  When I go to System>Administration>Network, the wireless connection wifi0 is activated.

It appears as though a driver is loaded for the device - here is the output of lshw:

*-network:1 DISABLED
[INDENT]description: wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: b
bus info: pci@00:0b.0
logical name: wifi0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical wireless Ethernet physical
configuration: broadcast=yes driver=hostap driververion=0.4.4-kernel firmware=0.0.0 latency=32 multicast=yes wireless=IEEE 802.11-DS
resources: iomemory:d7000000-d7000fff irq:10[/INDENT]

I am a little concerned about the "DISABLED" part.  I was able to find reference to this but everything was about a laptop...I have a desktop.

iwconfig for wifi0 shows: IEEE 802.11-DS mode:managed

I sincerely appreciate any suggestions.

---

### Post by rvergara on 2007-07-21
I had a similar problem with DWL-122. Try this:

sudo ifdown wlan0

and then 

sudo ifup wlan0

This just cycles up and down your wireless connection. It worked for me.

Let me know if that helped.

Regards

Ramiro

---

### Post by wak_maximus on 2007-07-21
i using a laptop...
this is my wireless card..
Intel (R) Pro/wireless 3945ABG...
i can connect to wireless using windows..however not in feisty fawn..
why??::cry::

---

### Post by Airist on 2007-07-21
I tried this and it didn't seem to change anything.  When I tried ifdown it came back with several lines and said something about a PID file already existing and that the SET FAILED.  I tried the ifup and it had several lines that said the network is down.  Thanks for the tip though.

---

### Post by annda on 2007-07-21
@wak_maximus: the intel card is supported by ubuntu. go to system>administration>restricted driver manager and check the driver. this will install the restricted kernel modules. reboot and everything should work fine. if not, post back.

---

### Post by annda on 2007-07-21
> **Airist said:**
> I tried this and it didn't seem to change anything.  When I tried ifdown it came back with several lines and said something about a PID file already existing and that the SET FAILED.  I tried the ifup and it had several lines that said the network is down.  Thanks for the tip though.

what about wifi0 instead of wlan0? what does your ifconfig say - is it wlan0 or wifi0? and do you happen to have the wlan switch turned off?

---

### Post by Airist on 2007-07-21
I have tried with wlan0 checked and unchecked...doesn't seem to make a difference.  I ran the ifdown and up on both the wlan0 and the wifi0.  

The device was not listed in the "Restricted Driver" form.  The only option in there was for 3D graphics through my video card.

Is there more information I can provide that would be helpful?

---

### Post by Airist on 2007-07-21
I don't see either wlan0 or wifi0 when I run ifconfig.

---

### Post by rvergara on 2007-07-21
Airist,

Annda is correct, i did not notice that the name of your interface is wifi0 so you should try with that interface. If this does not help can you please paste here the output of "ifconfig"?

Regards

Ramiro

---

### Post by annda on 2007-07-21
plaesa check ifconfig and iwconfig and post the output of both.

---

### Post by Airist on 2007-07-21
Sorry it took a while to get back...I don't have a printer on that computer so I had to write everything down by hand for you.  Here is the result for ifconfig:

Etho
Link encap:Ethernet HWaddr 00:03:B3:01:85:05
inet6 addr: fe80: ::203:b3ff:fe01:8505/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address: 0xd000

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:190 errors:0 dropped:0 overruns:0 frame:0
TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14212 (13.8 KlB) TX bytes:14212 (13.8 KlB)

---

### Post by Airist on 2007-07-21
Resuts for iwconfig are as follows:

lo        no wireless extensions.
eth0   no wireless extensions.
wifi0   IEE 802.11-DS Mode:Managed
          Link Quality:0 Signal Level:0 Noise Level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by rvergara on 2007-07-21
Can you go to synaptic and check if linux-wlan-ng is effectively installed?, if not please install it

Ramiro

---

### Post by Airist on 2007-07-21
Okay this is where my "first day user" status is going to be painfully obvious.  I opened up synaptic and linux-wlan-ng is not on the list.  I searched for it, but nothing was found.  How do I get this on the list so that I can install it?

---

### Post by wak_maximus on 2007-07-21
> **annda said:**
> @wak_maximus: the intel card is supported by ubuntu. go to system>administration>restricted driver manager and check the driver. this will install the restricted kernel modules. reboot and everything should work fine. if not, post back.

thanks..it works now..
i'm asking this because i can't update using update manager..
some files were failed to download..(404 Forbidden)..
but here i more think..
in windows..if i connect to wireless connection..
at the time i open the internet browser...
it will directing me to login page..
because wireless network is provided from my college administration...
since i'm in college..:)so why in Ubuntu, i don't have this login page??:confused:

---

### Post by rvergara on 2007-07-21
Airist,

do not get frustrated. We are getting closer. You do need the prism drivers in order for wifi to work. Go to synaptics again and make sure that in the repositories tab you have all of them checked with the exception of sources. linux-wlan-ng should now be listed.

You need linux-wlan-ng in order for your prism based card to work.

Ramiro

---

### Post by Airist on 2007-07-21
I appreciate your patience with me and your willingness to help.  I opened synaptics again and found "repositories" under "Settings".  Everything was checked except for "Source Code".  Back to the synaptic list, I made sure to list "All".  Would linux-wlan-ng be the package name?  If so, I still don't see it listed and can't find it through the search.

---

### Post by rvergara on 2007-07-21
I assume you are using Ubuntu 7.04, right?

Yes, that is the name, I uploaded a screenshot of my synaptics window

Ramiro

---

### Post by Airist on 2007-07-21
Yes, I have 7.04 Fiesty Fawn.  My screen looks like yours except it is in english and does not have the same packages.  I found a blog by someone who said they they also did not get linux-wlan-ng as part of the install.  They downloaded it and installed it somehow.  I found where to download it.  I burned it to a CD, but have no clue how to install it so that I can see it in the list.

---

### Post by Airist on 2007-07-21
Okay, I got linux-wlan-ng installed!  Had to download it, but it's there now.
Everything still looks the same.

---

### Post by Atomic Dog on 2007-07-21
> **wak_maximus said:**
> i using a laptop...
this is my wireless card..
Intel (R) Pro/wireless 3945ABG...
i can connect to wireless using windows..however not in feisty fawn..
why??::cry::

I have the same wireless card and it worked out of the box with Feisty.  You should not be having this problem.  Make sure it is enabled and the intel 3945 driver is listed and enabled in the restricted drivers applet.

---

### Post by jppaynesr on 2007-07-21
For me, Ubuntu as configured out of the box was not easy to set up using WiFi until I heeded the advice given here. Get WICD, [http://wicd.sourceforge.net](http://wicd.sourceforge.net). It will solve your problems. Follow the instructions, including the part about removing the network manager using Synaptic.

Let us know if it solves your problems like it did for me.
My only gripe is the network does not always reconnect after a resume from suspend, but it is only 3 clicks to get it back.

---

### Post by rvergara on 2007-07-21
same ifconfig and iwconfig output?

Ramiro

---

### Post by rvergara on 2007-07-22
I googled around for your problem. What dwl-520 do you have? what revision?, there seems to be large differences, even different chips, among the different revision of the dwl-520.

Ramiro

---

### Post by Airist on 2007-07-22
The official title and version is...

D-Link Air DWL-520e1 
2.4 GHz/802.11b Wireless PCI Adapter

---

### Post by rvergara on 2007-07-22
Airist,

Apparently revision E1 is not one of the easy ones. They lack firmware so needs the so called hostap drivers. Fortunately these have been included in Ubuntu from 6.06.

Follow instructions listed here:

[http://82.211.81.186/showthread.php?t=198568](http://82.211.81.186/showthread.php?t=198568)

You need mostly to blacklist the orinoco drivers. At the end of the process you should have a wifi interface listed in ifconfig and signal coming listed in iwconfig although some users are reporting to still having difficulties. If this fails for you my best advice is to read in the forums recommended cards and buy a new one.

Really hope this helps, whatever the case please report back so other users can learn from your, hopefully, success or failure.

Regards

Ramiro

---

### Post by trucker33377 on 2007-07-22
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) 

this helped me. also check to make sure your wifi is supported. i just went to frys and got a netgear wg 111 v2 pluged in and it worked

---

### Post by Airist on 2007-07-23
Thank you for your help.  I will try the links provided and will post the outcome.  I have learned a lot from this issue but may have to resolve by purchasing a new card...no biggie.

---

