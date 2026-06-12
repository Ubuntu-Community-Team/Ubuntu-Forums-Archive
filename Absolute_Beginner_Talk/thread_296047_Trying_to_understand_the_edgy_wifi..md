---
title: "Trying to understand the edgy wifi."
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-09
Hello, I was wondering if anyone has the time to explain a little about the wifi in xubuntu edgy. 

In windows xp, all I had to do was open the wifi manager, and I would see a list of wifi router addresses that I could link to. If I wasn't seeing an address that I knew was there, then I could just click the "refresh" button and I would see a new list of available addresses.

In xubuntu 6.0.6 and 6.10, I was able to install my broadcom airforce1 internal wireless card's drivers from this ubuntu forum tutorial: [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

I used the first option of step 2) by downloading the drivers from this link: [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

Well, after I rebooted and connected my wireless, the blue LED light on my notebook (hp pavilion dv4230us) turned on like it does when using windows xp (it had been off before installing the drivers).

So I figured that I had installed my wireless correctly and would find out when I needed to since I don't have a wireless router connection at home.

Now, I went out the other day and I drove to some areas that I have used my Xp's wireless card to see if my xubuntu edgy wireless was working at the same locations. 

Well, I didn't see any new ip addresses or any list of addresses or routers like Linksy to connect to at a few places that I know have wireless streams. I saw no detected streams on my Network monitor on my panel while driving around searching for wireless steams in areas that I know have wireless available.

At this one place that I know was a wireless connection, I kept clicking on  the General-->--Automatic Service Discovery and all of a sudden my Network Settings broke, half of it disappeared leaving only the top window tool bar. My panels, both top and bottom also disappeared and I was unable to fix that problem. I could still get back to the settings of the Network Settings by using the drop down menu of a right click.

I know this is sort of a "hold my hand" thread and teach me how to use my wireless properly thread, but a link to a good instructional guide and way to configure the settings or any info on how to use the wireless would be cool.

Also, in step 2) of the driver donwloads, would it be better to use the exact driver from my /Windows/System32/Drivers/bcmwl5.sys ???? 

Thanks to anyone who takes the time to respond,
-c.

As for the disappearing panels, I ended up having to reinstall again because I messed my system up trying to fix it with terminal. At this point I would like to start only using xubuntu with a smaller back up partition of Xp, if I could have my wireless working correctly.

---

### Post by crimesaucer on 2006-11-09
No prob... I'll learn on my own, I always do.

---

### Post by casperiv on 2006-11-09
I agree about the learning curve coming from XP.. I expected a simple manager like XP had and got confused when I didn't get one.  I was further confounded when I tried to find how to select the network I wanted to connect to and didn't even see a screen that said "No networks detected" or hinted that the card was even working.  

I have seen a few people had that I really liked, but I don't remember what they were off hand.  I do know at least one of them was downloaded from our wonderful app getter.

---

### Post by fatneck on 2006-11-09
Thanks for your link as I have been banging my head for 2 weeks on this. I can't really help you unfortunately except to say that no sooner had the wireless started to work than Network Manager told me there was no connection working.

I'm now unsure as to how I will change the wireless connection when I go into the office and try to use it there.

Instinct says to uninstall and re-install Network Manager into an environment where wireless is up and running and that it will find its feet that way.

---

### Post by crimesaucer on 2006-11-09
So casperiv, you were saying there is a "document" that explains the wireless and how to use it available in synaptic? Thanks, I'll search for it and if I find it I'll post it.

...and yeh, this wireless is a bit more confusing than Xp, I don't even know where the wifi signals to connect to show, I looked under Host and DNS and didn't see anything like "Linksy" or "Belkin", maybe I need to connect in a different way to see the available signals. 

Also my Network Monitor on my top panel won't show any signal at all when driving through my neighborhood that has a lot of wifi routers available.

Incoming: 0.00 kBytes
Outgoing: 0.00 kBytes

I figured that the driver/firmware from the tutorial worked since my antenna light turned on after installing it from that guide, so maybe I need to learn proper configuration.

As for installing in an environment that already has a wifi signal, sounds like a good idea, maybe it will auto-detect.

---

### Post by casperiv on 2006-11-09
Mine did that when it wasn't actually working but detected.  Have you actually got it connected to an access point?  My wifes desktop is working great, but my laptop had some strange issues with the onboard wifi.

My wireless detected, showed in devices as working, showed in networking as eth1, but never said it was recieving or sending no matter what I did (And I was sitting a foot from my router).  I tried everything and got no where.  No matter what I did it would not activate or connect to anything.  I ended up blacklisting that driver and trying different drivers and following some how-to's on the forums.... without luck.  I am going to be fighting with it again later today, and I am hoping to have an answer to as why it wasn't working.

The laptop in question is my AMD 64 Gateway MX7118, and the wireless is the only thing not working at the moment.

---

### Post by fatneck on 2006-11-09
You have an HP laptop too don't you? I just turned the wireless/bluetooth button off and the wireless died straight away. Turned it on and nothing happened, no internet. Rebooted with the light on and it came straight back up. So the questions for me, and possibly for you too are:

What takes priority between:

1. The physical button on the machine that turns wireless on/off.
2. Ubuntu's built in Networking utility.
3. Network Manager.
4. Anything else?

Going to uninstall Network Manager and see what happens. Not really helping your original post here, but I think we are kind of on similar issues.

---

### Post by crimesaucer on 2006-11-09
Check this package that was recommended to me on another forum: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

This looks like a better way to search for available signals by just using one terminal command of: sudo wifi-radar -d

I don't have a wifi router at home, I only use wifi when I leave the house so I won't know if it works today.

I was also told that you need to set your wifi settings to a static Ip address for the router the first time, so it recognizes and connects to the router. If this works, let me know

---

### Post by crimesaucer on 2006-11-09
In my opinion, the wifi radar works because I am now able to detect my neighbors Linksy router, I don't have the security access numbers to test it as a working signal, but at least it can detect it. And it says Linksy instead of a list of IP addresses.

Also, for the network manager, I'm wondering if I select this [ff02::2  ip6-allrouters] from Hosts menu, that it might detect hotspots to connect to since I don't have an actuall "static ip" to use since I have no home router.

Anyway, I probably don't need to mess with the network manager because the "wifi radar" seems like what I needed anyway to detect hotspots and connect easily to random wifi signals. It even has a signal strength system like Xp had with the bars.

good luck and I hope this helps.

---

### Post by fatneck on 2006-11-09
Wifi Radar seems to work as it has picked up a few signals that I know are there from running Windows. Doesn't seem to want to let me EDIT the options though, or even give me an option to CONNECT to the other networks that it can find...any ideas?

Just tried Network Manager and again it has come up with no network and a red cross through it despite me being wirelessly connected. Bye bye Network Manager.

So still not quite sure how I'll connect to the office network when I next go in there - anybody got any ideas why Wifi Radar won't let me connect etc?

Cheers

---

