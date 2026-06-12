---
title: "[SOLVED] ****Need assistance in wireless section****"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Lazy-buntu on 2008-04-11
I don't know how common this problem is, but here goes. I'm dual booting Vista (where I'm typing now) and Gutsy Gibbon (32bit). I've got ndiswrapper working with the correct driver, my wireless card can scan and see networks, but I'm unable to connect to my network/the internet.

I use 128 bit WEP, a broadcasted ESSID, and my router acts as a DHCP server. I've got a thread going in wireless section: [http://ubuntuforums.org/showthread.php?p=4692890#post4692890](http://ubuntuforums.org/showthread.php?p=4692890#post4692890)

I think the problem has to do with the DHCP, I posted on the second page the output of sudo dhclient wlan0.

Also, I have the same problem with a wired connection. However, if I use Fedora 8 or OpenSUSE 10.3 Live CD I can use wired connection no problem (but in OpenSUSE my sound doesn't work and in Fedora I have no mouse pointer--either way I like ubuntu better than both)

I'm running out of options..please help :(

---

### Post by bilal.17 on 2008-04-11
for me it would not work in connecting until i installed a different program to manage connections such as wifi radar

---

### Post by zvacet on 2008-04-12
I hope [this](http://ubuntuforums.org/showthread.php?t=684495) will be helpful to you.

---

### Post by Lazy-buntu on 2008-04-12
@bil  I can't get a wired connection to download wifi-radar, I'm going to try and download it from the windows half of my dual boot and just extract the package on the ubuntu half.

@zva I tried that before, it didn't help :(

---

### Post by Lazy-buntu on 2008-04-12
Ok figured out how to download it, I'm  gonna head over to the ubuntu side of my dual boot, wish me luck!

---

### Post by shivam.seth on 2008-04-12
which wireless card are you using?.....are you using Broadcom wireless card?.....if yes...then you might have problems with Broadcom and ndiswrapper combo. For some people it just works fine but I also had somewhat similar problem as yours with this combo. So I finally had to switch to Broadcom native bcm43xx-fwcutter instead of ndiswrapper.

---

### Post by kaginken on 2008-04-12
In addition to posting your wireless model try opening up your wi-fi security wide open.  That is, disable the encryption, mac filtering, etc then try it.  Try to get it connected first, then start locking the router back down one thing at a time.  

Hope that helps!

:guitar:

---

### Post by Lazy-buntu on 2008-04-12
Wifi-radar didn't work, still having a problem accepting DHCP offers.

I am using a broadcom card: problem is I can't get a wired connection with ubuntu (although I can with Fedora 8 or OpenSUSE 10.3 Live CDs...)

I heard fw-cutter works well with this card, but unless I can download it on vista and copy the package over, I can't use it.

I'll see if that's possible.

As for the security, I don't have MAC filtering on, and I don't want to disable WEP (even if it's temporary) because there are so many devices already configured and using the WAP intermittently (I can think of 7 or 8, not all using at once of course).

I'm going to take a look into fw-cutter right now.

---

### Post by Lazy-buntu on 2008-04-12
I think I'm going to reformat, reinstall, and try just fwcutter (since I've got changes to all sorts of things), unless there's some sort of system restore:

Is there a way to restore the system back to fresh install state?

---

### Post by Lazy-buntu on 2008-04-12
fw-cutter worked worse than ndiswrapper (wouldn't work after reboot)

i'm back with my original setup with ndiswrapper, same problem:

ubuntu won't accept and DHCP offers

---

### Post by bt224 on 2008-04-12
Make sure Roaming Mode is enabled. Should be by default, but you never know.

---

### Post by Lazy-buntu on 2008-04-12
I don't know what to do. I would prefer to get gutsy working, but I could always try hardy heron beta (::shudders::), or I could go to Fedora 8 and try wireless there (atleast with Fedora I have a wired connection)...it sucks that gutsy doesn't have better HP laptop support.

Still open to ideas on gutsy not taking DHCP offers though.

---

### Post by kaginken on 2008-04-12
Must you use DHCP?  You can always set a static IP...

---

### Post by elmer_42 on 2008-04-12
Is there any reason you have to have DHCP? I mean, if you think it's the problem, it's worth the shot, right? Just set your IP to something that the DHCP doesn't use. I'm not sure what router you have, so I don't know at what number your DHCP starts.

---

### Post by Lazy-buntu on 2008-04-12
I guess I could try using a static IP address, but if I ever take my laptop outside my home I'll run into problems (unless I use Vista).

Let me try that real quick.

---

### Post by Lazy-buntu on 2008-04-12
DHCP is from 192.168.2.2 to 192.168.2.199

so i tried 192.168.2.201 with no luck, I don't have too much time to mess with this though until late tomorrow or monday though

i'm working on a c++ program right now that isn't going too well lol

anyway thanks for the input

---

### Post by Lazy-buntu on 2008-04-12
I downloaded Hardy Heron Beta Live CD and good news..I've got a wired connection (can't get in gutsy even in live cd)!!! I'm going to install it tomorrow and hopefully I'll be on my wireless connection.

I'll let you know how it goes tomorrow :)

---

### Post by russo.mic on 2008-04-13
Well,  Hold the phone for a sec, lets do some prodding around.

First of all, I would try to connect from the command line.  I'm gonna guess you can't.  But we need to find out.

After you boot up, from a terminal type:

ndiswrapper -l and make sure it says the driver is installed and that the hardware is present.

next, give it the ole "rmmod ndiswrapper" then "modprobe ndiswrapper"

after that, type "iwconfig".  Do you see your wifi card?  wlan0 or something? 
if so, type "sudo wconfig 'name of card here' essid any"  i.e., I would type:

iwconfig wlan0 essid any

If all this goes well, you should be able to hit iwconfig and see your network name.  After that type "sudo dhclient" and you should be connected!  
Let us know what, if any, step fails.  I'm guessing that you probably have the wrong driver for your wireless card, as I've delt with this before.  

Good Luck!

Russo

---

### Post by Lazy-buntu on 2008-04-13
I couldn't even get a wired connection in Gusty, but in Heron I can. In gutsy I can see the network names, I can even get packets sent and returned, but if I go to do dhclient I get:

sudo dhclient wlan0


Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on Socket/fallback
ubuntu-dualboot@ubuntu-dualboot-laptop:~$ sudo ifconfig eth0 down
ubuntu-dualboot@ubuntu-dualboot-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

and keeps going....

---

### Post by Lazy-buntu on 2008-04-13
Okay, I tried Hardy Heron, and it didn't act as well as the live cd did, but there's some good news.

Gutsy Live CD was letting me use a wired connection in roaming mode. I installed gutsy (yet again), but DHCP was acting screwy again. Anyway, I assigned a static IP address for the wired connection so that's how I'm posting now,

Gutsy did the upgrades, I added the restricted ubuntu extras for flash and mp3s etc, but **before I fool around with drivers I need to know if I can create the equivalent of a windows restore point?**

Thanks for your patience :)

Also, any recommended apps? After I get my nvidia drivers working (which will be after I get the wireless working) I would like to get the cube desktop working--is that through compiz?

:guitar:

---

### Post by Lazy-buntu on 2008-04-13
I heard that there is a driver for my card:  BCM94311MCG wlan mini-PCI (rev 01) is not compatible with 128 bit WEP...i'm not totally sure, but I'll look into it

---

### Post by Lazy-buntu on 2008-04-15
messed around with wireless for a week, reformtatted many times, now I use PCLOS 2008 Gnome--which didn't even require manual installation of ndiswrapper or the bcmwl5.inf driver

just went to configure my computer, network/internet, wireless, ndiswrapper, chose bcmwl5.inf, popped in my WEP key and bam had wifi (didn't even had to reboot)

---

