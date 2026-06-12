---
title: "madwifi dhclient macbook connecting issue"
date: 2008-03-29
forum: Apple Intel Users
---

### Post by dustynus on 2008-03-29
My madwifi drivers work fine ( I suppose)

I'm using macbook santa rosa, duo core intel. Feisty 7.10, installed following ubuntu wiki directions.

I had wireless working and connecting fine in a previous install...now though I have issues:

All the networks show up fine in the network manager, when I select a network to connect to, it just keeps loading it, it never gives me an ip.

I try to connect manually:

sudo iwconfig ath0 essid "whatever"
sudo ifconfig ath0 up
sudo dhclient ath0

When I do the dhclient ath0 command, it just keeps trying, and it never succeeds on any network.
> stox@stox-laptop:/tmp/madwifi$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 8843
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:e3:da:42:de
Sending on   LPF/ath0/00:19:e3:da:42:de
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
stox@stox-laptop:/tmp/madwifi$ 


Am I missing something ?

Thanks :)

---

### Post by cyberdork33 on 2008-03-29
why are you not just using network-manager?

---

### Post by dustynus on 2008-03-30
That's the problem, network manager doesn't give me an ip. It just keeps loading it
It's shown as in "roaming mode", and I can see the list of essid's, but it just keeps loading when i select one


Thanks,
Mike

---

### Post by cyberdork33 on 2008-03-30
well if you are going to set things manually, you have to turn the roaming mode off then. The WiFi card seems to be working ok, it is just not communicating with your AP very well. Can you try without any type of encryption on the connection and see if it works then?

---

### Post by Infinite Recursion on 2008-03-30
I'm having the exact same problem.  The list of APs appears in the Network Manager, but it refuses to get an IP address.  It tries to connect for several minutes, and then gives up.  This behaviour doesn't seem to be linked to any sort of encryption - open networks do the same thing.

What seems odd to me is that when I was using Ubuntu 7.10 AMD64, wireless worked beautifully; I never had this problem.

Edit: The only difference that I can see from what has been posted is that I am using a 2nd Gen MacBook (C2D), rather than a Santa Rosa.  Madwifi revision is 3407, if that helps.

---

### Post by dustynus on 2008-03-31
with no encryption, exact same problem. I'll try messing with it a bit tomorrow, the wifi card does work fine, I was thinking it was dhclient that was messed. Is there a way to reinstall dhclient or configure somehow to use the madwifi drivers properly ?

Thanks for your help
:guitar:

---

### Post by kingducttape on 2008-03-31
Having exact same issue.  Any help would be much appreciated.  Thanks!

EDIT:  SantaRosa MBP, ubuntu 7.10

---

### Post by sheffrem on 2008-03-31
i use 7.10 to but 64 bit versions. May be by using the 64 bit will make it work just like mine does.

---

### Post by kingducttape on 2008-03-31
I'm also on 64-bit, but am having the problem.

---

### Post by trouble1313 on 2008-03-31
Hate to sound negative but I've just plain given up on madwifi and network-manager. I jumped through hoops over and over trying to make it work reliably to the point where I was checking out revisions daily from madwifi cvs (I'm not convinced it's updated at all anymore) and even gave ath5k a shot just for grins. Still just never worked well...some times it would connect...sometimes not, same access points, same locations, but even when it would connect, the throughput speed and connection stability  was far lower than what I get in Vista or OSX. On the good days when it would connect I'd still face around 30 seconds of the thing connecting every single damn time my laptop resumed from suspend.  I've gone to OSX pretty exclusively now on my mbp unless I need something specific in Linux and have a wired connection available. Yeah I could downgrade to 32 bit and go the ndiswrapper route but I really don't want to. Over time I became more and more convinced that the problems lie with network-manager and not entirely with madwifi.  I have even gone to Hardy and face exactly the same things I faced in Feisty and Gutsy. It's quite dissapointing...It was super painful to get used to macos!
-Trouble

---

### Post by dustynus on 2008-04-01
I did figure out how to make the wireless work.
The network manager, can't figure out how to get it to get the ip still..

If you go and disable roaming mode, and then select the network you want, then select DHCP.

Open terminal:
> 

sudo iwconfig ath0 essid network key restricted s:password
sudo ifconfig ath0 up
sudo dhclient ath0



Change ''network'' and password'' to your password and network you want.
if it's an open network type:  "sudo iwconfig ath0 essid network"

That should work for you guys. I'm amd64 on 7.10

If anyone finds out how to get this actually working with network manager that'd be great

---

### Post by cyberdork33 on 2008-04-01
you can use ndiswrapper on either 32 or 64 bit as long as there is a windows driver available.

ath5k has not been updated to handle the Mac chipsets yet (please help them if you can!) and the older madwifi is not being updated anymore (much).

---

### Post by dustynus on 2008-04-01
Thanks for the info :)

---

### Post by trouble1313 on 2008-04-02
Woah, Cyberdork, have you found a 64 bit XP driver for the Atheros card? I've never been able to find one and the Vista NDIS6 drivers don't work with ndiswrapper (yet).  I'd almost kill to get one!
-Trouble

---

### Post by cyberdork33 on 2008-04-02
> **trouble1313 said:**
> Woah, Cyberdork, have you found a 64 bit XP driver for the Atheros card? I've never been able to find one and the Vista NDIS6 drivers don't work with ndiswrapper (yet).  I'd almost kill to get one!
-Trouble
I didn't say that. and judging by your response, I would assume that there isn't one anywhere.

---

### Post by trouble1313 on 2008-04-06
Ok, seeing this thread last week made me go and futz around some more to nail things down. My Vista install ate itself somehow so I figured I'd start fresh with new partitions etc. I went 32 bit Hardy this time so I could check out ndiswrapper for the ar5418.

The problem...Network Manager. It exhibits the exact same issues with madwifi or ndiswrapper.  Manually setting up the wireless connection works fine (well fine 90% of the time which is WAY better than what I was getting previously.) I went ahead and ripped out network manager altogether and threw wicd on and it continued to be pretty good. Static mapping for wireless in /etc/network/interfaces is the ideal situation but that's only marginally useful for me since I'm always traveling with my mbp. So while madwifi certainly has issues, it doesn't seem to be the cause of all this connection pain. That damn network-manager is what I think is doing it now. Watch your /var/log/daemon.log and you should be able to see that the hardware sets up fine and then network-manager gets upset retrying dhcp. 

So you can give wicd a try if you feel like it and maybe it'll behave itself better. It's not as nicely integrated but hey it's better than nothing.

-Trouble

---

### Post by deb on 2008-04-06
This post may be of some help....[http://ubuntuforums.org/showthread.php?t=738117](http://ubuntuforums.org/showthread.php?t=738117)
though this is for hardy, i would first remove network manager using sysv-rc-conf and unchecking all the X s.

then I will modify the /etc/network/interfaces file to look like in the post.
then will issue sudo /etc/init.d/networking restart

if that does not work in Gutsy 7.10 (not sure what is Fiesty 7.10) then I will use this (madwifi-ng-r2497-20070622.tar.gz \cite [http://ubuntuforums.org/showthread.php?t=587828](http://ubuntuforums.org/showthread.php?t=587828)) madwifi driver folder to make, sudo make install, sudo modprobe ath_pci and then restart the machine... after restart i will issue sudo /etc/init.d/networking restart and pray that it works... sad state of affairs.

I have a copy of the above driver if you do not find it anywhere else :).

---

