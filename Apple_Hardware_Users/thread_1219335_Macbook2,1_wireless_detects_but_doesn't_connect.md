---
title: "Macbook2,1 wireless detects but doesn't connect"
date: 2009-07-21
forum: Apple Hardware Users
---

### Post by tripundra on 2009-07-21
Hi,

I've been trying to put my wireless to work and it doesn't seem to want.

I've got a Macbook 2,1 with the atheros chipset. I'm using Jaunty.

I've installed the backports and use the wicd to control network use.
It detects the networks, but it does not connect to them. keeps on trying an nothing happens.
I've ven tried Ndiswrapper.
With ndiswrapper selected on wicd I get more networks than with Wext or Madwifi, but can't conect to them. I've tried Open WEP and WAP2.
On a previous installation it was working perfectly! But this time, doing exactly the same as last time it doenst!


Hope anyone has some good Ideas,

---

### Post by tiagobt on 2009-07-21
My wireless driver has been very unstable with the latest upgrades as well (MacBook 2,1 + Jaunty). The wireless networks are detected and sometimes I can connect to them, but no websites are found. In KDE, my attempts to connect to wireless networks made the entire system unresponsive (default Network Manager plasmoid). I tried using [volanin's patch](http://ubuntuforums.org/showthread.php?t=1217022), but I noticed no improvement.

Does anyone know what's happening? The driver was working just fine a few weeks ago.

Thanks,
Tiago

---

### Post by Richardcavell on 2009-07-21
I have the same problem with my MacBook2,1, with the wireless setup able to view all available wireless routers but often unable to connect.  I am almost always able to solve it by restarting the computer (logging on and off doesn't seem to be enough).

Mind you, I also get that problem under OS X.  I think it's the wireless hardware that is at fault.

Richard

---

### Post by NJLash on 2009-07-22
I'm having the same problem on my 2,1.  I never had this problem on arch or os x.  My computer connects fine to my Airport Extreme network at home, but it doesn't seem to want to connect to other wireless networks.
I think it could be a problem with dhclient.  It won't give me an address.  I used dhcpcd on arch, and it worked very well.  I can't try it now, as I am at a cafe, and have no connection on Ubuntu, but I think that could work...maybe...
Sadly enough, I am writing this on OS X.  I hope this gets resolved, so I can be on ubuntu all the time.

---

### Post by tiagobt on 2009-07-22
Same thing here. Wireless works just fine in Mac OS X, so it's not a hardware issue. In my case, DHCP seems to work because I'm assigned an IP address (at least Network Manager shows an IP). However, I've been trying to connect to my home network the whole time, so the IP might have been kept somehow, as NJLash mentioned.

Is it time we filed a bug? The only problem is that we haven't found the source of the problem yet..

---

### Post by mabovo on 2009-07-23
Wicd instead of Network Manager is a good solution.

---

### Post by NJLash on 2009-07-23
so far so good with wicd.  We'll see what happens when I go to the cafe tomorrow...

---

### Post by tripundra on 2009-07-24
I think I managed to solve it, at least partially.
It's not hardware fault as with MaxOSX it connects with no problems.
I am using Wicd.
Wep connects fast, unsecured wifi's take a little bit longer but ok.
WPA I need to specify a IP. connect. Remove the fixed IP to assigned by router and then disconect and connect again.
I have a Belkin router in the house, so I usually asign the IP i know is going to be free. When it reconnects it uses the same IP! sometimes one above or below.
Strange.

---

### Post by NJLash on 2009-07-24
Well, wicd, along with the backports, seemed to fix my problems!  ...so far so good!

---

### Post by tiagobt on 2009-07-26
I still have the problem. I found out what was making the system unresponsive: I had a remote partition mounted, and this "fake" connection was making smbfs unstable. I unmounted the remote partition and tried using Wicd, but the behavior is the same: I can see all the wireless networks, I can connect to my own network, I get a valid IP address, but I'm not able to browse the local network or the Internet. I'm not sure this is relevant, but I use Kubuntu instead of Ubuntu.

Thanks,
Tiago

---

### Post by tripundra on 2009-07-27
just to keep an update..
I no longer need to do all those steps... it does take a few tries to connect thow.
so far so good...

---

### Post by tripundra on 2009-08-08
Changed to Ubuntu from studio and all is well now... Network MAnager is working better than WICD I might had.(amazing)

---

