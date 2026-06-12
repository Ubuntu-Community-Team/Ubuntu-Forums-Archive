---
title: "Network Manager VS Wi-fi radar"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-08-06
Which one is better? Are they the same? I downloaded both and when I finally got my wi-fi card to work, I was using network manager. All of a sudden, network manager stopped working (wi-fi radar still works though). Why won't network manager connect to any networks anymore? Why does wi-fi manager connect to networks with ease?

---

### Post by friedokra on 2006-08-07
bump.

---

### Post by bensexson on 2006-08-07
Neither worked for me with a hidden SSID.  If wifiradar would work it would be better because it starts at bootup before X starts.

---

### Post by Metacarpal on 2006-08-07
I've never had any problems (per se) with network-manager, but I use WiFiRadar anyway.  For me it's a question of lower time-effort in switching networks.  I added a launcher for WifiRadar in my Launcher, so I'm one-click from choosing a new access point, as opposed to right-click, properties, configure, etc...

---

### Post by mblind on 2007-12-07
Do you have to uninstall network manager to use wi fi radar?

---

### Post by walkerk on 2007-12-07
Try [WICD]("http://wicd.sourceforge.net")... and yes, it will remove Network Manager.

---

### Post by wieman01 on 2007-12-07
Uninstall Network Manager first, then install Wifi Radar or WICD. WICD is a better choice for Gnome users in my opinion.

---

### Post by stchman on 2007-12-07
> **bensexson said:**
> Neither worked for me with a hidden SSID.  If wifiradar would work it would be better because it starts at bootup before X starts.

Network Manager has its short comings with hidden SSIDs.  If you don't hide the SSID then NM has no problem.  There seems to be a big confusion among folks that hidden SSIDs actually improve security.  Hidden SSIDs actually do little to zero for wireless security.

---

### Post by wieman01 on 2007-12-07
> **stchman said:**
> Network Manager has its short comings with hidden SSIDs.  If you don't hide the SSID then NM has no problem.  There seems to be a big confusion among folks that hidden SSIDs actually improve security.  Hidden SSIDs actually do little to zero for wireless security.
NM can handles hidden networks, not on all computers for a strange reason, but it can in my case.

It does not really add extra security, I agree here, however, it makes a stand-alone router less vulnerable if the network name is unknown, because potential attacker are unable to precompute WPA passphrases without knowing the wireless network's SSID. As soon as a client connect that advantage is forfeited.

So it adds a **little** extra security, but not much.

---

### Post by stchman on 2007-12-07
> **wieman01 said:**
> NM can handles hidden networks, not on all computers for a strange reason, but it can in my case.

It does not really add extra security, I agree here, however, it makes a stand-alone router less vulnerable if the network name is unknown, because potential attacker are unable to precompute WPA passphrases without knowing the wireless network's SSID. As soon as a client connect that advantage is forfeited.

So it adds a **little** extra security, but not much.

There are some that say it actually is WORSE than nothing at all.  George Ou and Steve Riley have articles that you should read.

[http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx](http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx)

[http://blogs.zdnet.com/Ou/?p=454](http://blogs.zdnet.com/Ou/?p=454)

---

### Post by wieman01 on 2007-12-08
> **stchman said:**
> There are some that say it actually is WORSE than nothing at all.  George Ou and Steve Riley have articles that you should read.

[http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx](http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx)

[http://blogs.zdnet.com/Ou/?p=454](http://blogs.zdnet.com/Ou/?p=454)
Interesting read. Thanks for the links. The second one it fairly interesting, in particular in terms of the stuff said about wireless clients probing for SSID's and sending precious information while you run around with your laptop. 

That said, I'd be interested to know if Ubuntu (or say Network Manager) does a better job in that respect. There is only mention of Windows (XP and Vista), so I am not sure if the same applies to us. 

I'll do some research and post back if I find anything useful. Perhaps you can help me as well. We learn something new every day. :-)

---

### Post by crimesaucer on 2007-12-08
I prefer Wicd to both of those: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

...it has an easy to connect gui, with options to use OpenDNS servers for static dns or static ip, encryption, and scripts for the new beta.

It also has options for Wired Network, which I use for my OpenDNS.

---

