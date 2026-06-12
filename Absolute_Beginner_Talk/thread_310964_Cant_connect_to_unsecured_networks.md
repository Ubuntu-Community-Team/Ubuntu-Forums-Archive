---
title: "Cant connect to unsecured networks"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by johnmxg12 on 2006-12-02
Hey guys, i tried looking for an answer to this question but i couldn't find it.  i configured my wireless card to work at my home-network but when i go to public access Wifi connections, i can't get through.  iwlist scan brings up the different networks in range but when i try iwconfig eth1 essid "name" it doesn't work.  it says operation not permitted. thanks in advance for the help.

---

### Post by dolphinsonar on 2007-01-01
I installed Wifi-radar after having a similar problem, it did the trick for me.

---

### Post by meng on 2007-01-01
sudo iwconfig eth1 essid (name)
You need superuser privileges to run such a command. iwconfig without superuser privileges will only report information, you can't pass parameters to it to change settings.

---

### Post by JustinSDC on 2007-01-27
Thank you for reporting this!

I am having the exact same problem. When I go into a public wifi hotspot my Ubuntu laptop will not connect. if I grab another laptop, such as my MacOSX one, it has no problem connecting.

I haven't yet tried what has been suggested here; I plan to.  However, for the record I am using:

Dell Latitude D810 
Ubuntu Edgy v6.10 w/ the Gnome window manager
03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
I'm also using the Gnome Wireless Network Manager Applet.

I select the open wifi hotspot in the nm-applet and it looks as if its connecting but eventually it just "gives up."

Any insight would be appreciated. Thanks again Ubuntu community!

---

### Post by CoolHand on 2007-03-01
Has anyone found a solution to this?  I know what the problem is and it has nothing to do with root privs.  On unsecured networks there are two types of key settings.  In iwconfig you can set the key to "off" or to "open".  Most public hotspots are "open" and for some reason I can't figure out how to get it to take this setting.  I used to use Mepis and for a while I had it working on there if I manually entered "open" as the key.  I have tried everything I know to get it to work on ubuntu and I can't get it to go.  I am on a hotspot now and I'm forced to use an OS I hate because I can't get my Linux box to connect.  I am currently using network manager and I don't wish to switch so I hope there is another answer.

---

### Post by jasonsweet on 2007-06-08
I am bumping this back, because I am having the same problem.  No problem connecting to my wireless home network, but trying to connect to a public wireless unsecured network is impossible.  The network  program sees them.  I also use wifi radar, but while it sees the public networks, it won't connect.  I am a newb to this Linux and I am trying to get off Windows once and for all, this is the one thing keeping  on it.

I run Feisty 64 bit on an Dell 640m laptop.

---

### Post by Rocket2DMn on 2007-06-08
I think you probably need to enable Roaming from System->Administration->Networking
This seems to solve a lot of problems with networking.

---

### Post by Shilahr on 2007-07-23
> **Rocket2DMn said:**
> I think you probably need to enable Roaming from System->Administration->Networking
This seems to solve a lot of problems with networking.

This is my first post; I have been looking for possible solutions for a couple of hours now.
Dapper doesn't seem to have a roaming option, or if it does, I did not find it.

I am using wifi-radar, as gnome-network-manager refused to cooperate with my wireless card (bcm4318). WiFi is available and stable on WEP-encrypted networks, provided I have the key of course. However, when I try to connect to the open network at my university, wifi-radar sees the network just fine and also lists the correct name, but when I try to connect, it tells me that it can't get an IP. I have the same problem at a friend's place where an open wireless connection is available (I don't have access to the router).

If someone has a working solution for this problem for Dapper, I would really appreciate it - would hate to be forced to work under Windows (as I am right now) just because the network is NOT encrypted...

ETA: Actually, setting the key to "off" with iwconfig did the trick for me. 

```
sudo iwconfig eth1 key off
```

After that, I tried to connect to an unsecured wireless network again under wifi-radar, and it worked fine.

---

