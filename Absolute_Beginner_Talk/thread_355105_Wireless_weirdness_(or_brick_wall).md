---
title: "Wireless weirdness (or brick wall)"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by 2wheelsgood on 2007-02-06
OK, I STILL cant get wireless working!  I've been trying for hours to no avail!

iwconfig wlan0 gives:

802.11b/g link..  ESSID:"BTVOYAGER2091-21"
Mode:Managed  Channel=10 Access Points: Not-Associated
Bit Rate=11 Mb/s
Retry:on  Fragment thr:off
Link Quality:0  Signal level:0   Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

So I think my dongle is supported? (a wireless device appears in "networking").

It seems something else is not configured right since theres no signal strength etc.  Im pretty sure the ESSID, WEP code are right.

Any ideas?  Ive only installed Xubuntu yesterday and REALLY dont want to be forced back onto windows so soon!

Thanks (a noobie)

---

### Post by Maxtorm on 2007-02-06
If you have a WEP key, I believe it would show in the output from iwconfig.  If you remove WEP are you able to connect?

---

### Post by 2wheelsgood on 2007-02-07
Thanks,

I've tried that though.  Even with the wrong/non-existant WEP code, I should stll be getting some singnal??

---

### Post by Ramses on 2007-02-07
What dongle is it? What does command lsusb print out?

---

### Post by 2wheelsgood on 2007-02-07
The dongle says "Dynamode" "WL-GI-700S".  As for the chipset, the windows drivers were Zd1211, which I think should be fairly well supported in Edgy?

For some reason I get "Command not found" with "Isusb" !!!??????? Maybe because im using Xubuntu???

---

### Post by 2wheelsgood on 2007-02-07
Im thinking that maybe the driver is wrong.  Should I just try to install the windows drivers with Ndiswrapper??

---

### Post by Ramses on 2007-02-07
I think there is command lsusb. You seemed to type Isusb there. Or was it just typo in message?

---

### Post by 2wheelsgood on 2007-02-07
Yes sorry! how do I get that symbol? (im not feeling clever today!)

---

### Post by Ramses on 2007-02-07
If the chipset is Zd1211, then maybe here is useful info [http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy]("http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy")

---

### Post by trippinnik on 2007-02-07
yes, please type 'lsusb'
that's like the ls directory command list, but for your usb devices.  this will give a hardware ID which you can search in Google to find out more info about you hardware.  If you have a zd1211 chipset dongle there are a couple of ways to get it working but it does require some configuration.  I have a dongle built on that a Planax miniusb54g.  shof2k has a good howto that uses the open source zydas drivers for linux.  I've gotten that to work, and also another method that I am using now (but it requires compiling your kernel).  here's the link: [http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy](http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy)

I am happy to help, but as some friendly advice please try searching the forums first, I noticed you posted 2 topics where there is already a Howto on your problem.  A lot of people are actually less likely to help out if you try to get help that way.  
That aside, goodluck with getting the wireless setup.  Unfortunately it is still way to difficult on most linux systems.  I bought a dongle with zydas chip because it had linux drivers and it was still a bit of work.  also I'd still like to know what lsusb puts out and also dmesg.

---

### Post by 2wheelsgood on 2007-02-07
thanks.  It looks a bit advanced for a newbie like me but ill give it a go....

---

### Post by 2wheelsgood on 2007-02-07
Thanks for you reply and advice trippinnik,

Im still trying to get the results from dmesg onto this windows machine to send to you!  Ill keep you posted, thanks...

---

### Post by trippinnik on 2007-02-07
cool, if you try dmesg right after plugging the dongle in you'll see the relevant information at the bottom of all the stuff right above your prompt. This way you don't have to worry about sending it all over. It'll probably seem like pretty advanced stuff, but you'll come to really appreciate all these extra tools when you've used them a bit.

---

### Post by 2wheelsgood on 2007-02-08
OK....I've attached the output of dmesg (wasnt to sure what was relevent!)

Also here is what I get for some other commands

iwconfig:

mike@TheBigBox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g  ESSID:"BTVOYAGER2091-21"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lsusb:

Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
mike@TheBigBox:~$ 

sudo lshw -C network: (the top entry being my working wired connection)

mike@TheBigBox:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: b
       bus info: pci@01:0b.0
       logical name: eth0
       version: 10
       serial: 00:07:e9:0d:86:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.1.5 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:febdf000-febdffff ioport:74c0-74ff iomemory:febe0000-febfffff irq:10
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 08:10:17:09:c4:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
mike@TheBigBox:~$ 

I also get "no scan results" for iwlist scan

The wireless dongle shows up in APPS-SYSTEM-NETWORKING but it doesnt pick up any available networks, so I just typed in my SSID/wep etc

Also I have a set of drivers (including linux drivers!) on CD if needed.  Im not to sure how they would be installed though (or even if I need them.  I think they need making, installing etc)

Many thanks for you time on this one!!!

---

### Post by 2wheelsgood on 2007-02-08
Sorry, but any ideas anyone???! Im considering throwing the computer out of my window... (or even worse, installing windows again!)...

---

### Post by 2wheelsgood on 2007-02-08
Also - when I previously installed Kubuntu (but found it too slow for my machine) I had some signal strength shown (although I didnt manage to connect to the internet).  Surely that must mean that my dongle is supported by in Xubuntu also?

---

### Post by trippinnik on 2007-02-08
well i am looking around at your dmesg now.  it reports the driver it is loading but it is an experimental driver and they ask you to report if it's successful (which seems like it is rare for it to work).  I am not sure if it is using anything related to the zydas chip.

---

### Post by trippinnik on 2007-02-08
i searched the forums for this: rtl8187 and found a number of threads.  I recommend checking those.  i don't know much about that card.  but there are also drivers for it located here: [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) and some information.  goodluck!

---

### Post by heri on 2007-02-08
> **2wheelsgood said:**
> The dongle says "Dynamode" "WL-GI-700S".  As for the chipset, the windows drivers were Zd1211, which I think should be fairly well supported in Edgy?

For some reason I get "Command not found" with "Isusb" !!!??????? Maybe because im using Xubuntu???

Hello,
*Newbie here*  My dongle has the same driver zd1211, it is 3Com 3CRUSB10075. 
And yes, after following this nice tutorial now it works fine:
[http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy](http://www.ubuntuforums.org/showthread.php?t=288753&highlight=zd1211+edgy)

I also tried Fiesty Fawn Alpha 3 and was very glad that the dongle was automatically recognized and I went online instantly.

---

### Post by trippinnik on 2007-02-09
Right, I have that chip and it's working too.  I've got the 2.6.20 kernel and the zd1211rw driver is built in.  I've also used this howto [http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211](http://www.ubuntuforums.org/showthread.php?t=354212&highlight=zd1211). but 2wheelsgood does not have a zd1211 dongle.  it's a realtek.  according to the USB ID, and the driver his system is loading.  I searched google for the USB ID, just like I did when I was trying to setup my own card.  This is why lsusb and dmesg are important.  I put in some links about setting up that hardware.

---

