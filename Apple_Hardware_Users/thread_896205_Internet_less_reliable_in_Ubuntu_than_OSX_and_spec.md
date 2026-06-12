---
title: "Internet less reliable in Ubuntu than OSX? and special characters"
date: 2008-08-20
forum: Apple Hardware Users
---

### Post by spencercarran on 2008-08-20
I actually have two questions to ask about. I installed Ubuntu Hardy on my Macbook 3,1 Santa Rosa and enjoyed it so far. 

However, I've run into an odd situation with my university's network. They do not support Linux (and have informed me of that pointedly) so I can't go the the uni tech center for help. After registering my laptop's MAC address (which should be the same regardless of what OS I use) with the network, I've found my internet connection (both wired and wireless) to be slow and unreliable on the Ubuntu side, while running fine on the few occasions I've booted up in OSX. I don't think it's a driver issue, since I went through ndiswrapper and all the rest to get that working, and internet worked just as well as in OSX back home. I know that's not much to go off of, but I'm pretty confused and don't know where to go from here. Any help would be greatly appreciated.

The second question about keyboard characters is more trivial, and one that I've been wondering for a while. In OSX, in order to type accents, you hit cmd-e before the letter you want accented, you hit cmd-u if you want the two-dot thingy over the next letter, and holding down alt gives you a separate set of characters on the keyboard- some Greek letters and also some random and occasionally useful symbols. Does anyone know how to enable something similar in Ubuntu? Not necessarily the same keyboard things as OSX, obviously, but some way of easily entering those into any text field without having to pull up a "special characters" menu and dig through it would be nice.

Sorry for the rambling post, and thanks in advance for any help.

---

### Post by cyberdork33 on 2008-08-21
> **spencercarran said:**
> However, I've run into an odd situation with my university's network. They do not support Linux (and have informed me of that pointedly) so I can't go the the uni tech center for help. After registering my laptop's MAC address (which should be the same regardless of what OS I use) with the network, I've found my internet connection (both wired and wireless) to be slow and unreliable on the Ubuntu side, while running fine on the few occasions I've booted up in OSX. I don't think it's a driver issue, since I went through ndiswrapper and all the rest to get that working, and internet worked just as well as in OSX back home. I know that's not much to go off of, but I'm pretty confused and don't know where to go from here. Any help would be greatly appreciated.Ethernet performance should not be different at all. You are right about your MAC addresses though (unless you change them ;) ). If you are getting poor(er) performance over ethernet in Ubuntu (or other distros...) than in OSX, my guess would be something about how they setup your school's network. 

Your Wireless on the other hand can vary in performance for a variety of reasons. First, although ndiswrapper has come a long way, it has never performed on par with real kernel drivers. Unfortunately, at the moment, that is really your only choice. This can be compounded depending on how the wireless APs are set. Is there encryption? How far is the AP? 

You also might want to check in the "networking & wireless" forum as this really should not be a specific Mac problem, and they may be able to offer more specialized help or tests you can do there.

> **spencercarran said:**
> The second question about keyboard characters is more trivial, and one that I've been wondering for a while. In OSX, in order to type accents, you hit cmd-e before the letter you want accented, you hit cmd-u if you want the two-dot thingy over the next letter, and holding down alt gives you a separate set of characters on the keyboard- some Greek letters and also some random and occasionally useful symbols. Does anyone know how to enable something similar in Ubuntu? Not necessarily the same keyboard things as OSX, obviously, but some way of easily entering those into any text field without having to pull up a "special characters" menu and dig through it would be nice.I think that this is only true on certain international keyboards, but yes, it is possible if you setup your xorg.conf correctly (and possibly your Gnome keyboard settings). The last thing you mention is (I think) the AltGr key (which is really different than a normal Alt key). [http://en.wikipedia.org/wiki/AltGr_key](http://en.wikipedia.org/wiki/AltGr_key)
Unfortunately, since I only use US keyboard layouts, I do not have these things, nor have I ever tried to set it up, but there are some posts in here and the archived Intel Apple forum about this that might be useful.

---

### Post by spencercarran on 2008-08-21
> **cyberdork33 said:**
> Ethernet performance should not be different at all. You are right about your MAC addresses though (unless you change them ;) ). If you are getting poor(er) performance over ethernet in Ubuntu (or other distros...) than in OSX, my guess would be something about how they setup your school's network. 
Wired is roughly 10x faster in OSX (by download speed, at least). Also, in Ubuntu it's often wired that is LESS reliable than wireless somehow. And the MAC addresses shown by ifconfig in Ubuntu are the same as the ones the tech people found in OSX and used to register my comp. (They got slightly annoyed at Ubuntu, and insisted that I boot up in OSX to connect me)

> Your Wireless on the other hand can vary in performance for a variety of reasons. First, although ndiswrapper has come a long way, it has never performed on par with real kernel drivers. Unfortunately, at the moment, that is really your only choice. This can be compounded depending on how the wireless APs are set. Is there encryption? How far is the AP? 
I'm not sure where the WAP is. Presumably there would be several across campus, since it's fairly large. I think there might be one in my residential college, but I'm not sure.

> You also might want to check in the "networking & wireless" forum as this really should not be a specific Mac problem, and they may be able to offer more specialized help or tests you can do there.
OK, thanks.

> I think that this is only true on certain international keyboards, but yes, it is possible if you setup your xorg.conf correctly (and possibly your Gnome keyboard settings). The last thing you mention is (I think) the AltGr key (which is really different than a normal Alt key). [http://en.wikipedia.org/wiki/AltGr_key](http://en.wikipedia.org/wiki/AltGr_key)
Unfortunately, since I only use US keyboard layouts, I do not have these things, nor have I ever tried to set it up, but there are some posts in here and the archived Intel Apple forum about this that might be useful.

Thanks again, I'll look into that, though right now I unfortunately am back in OSX because I was sick of having to relaunch my browser and constantly re-connect to the network. But I am using a US keyboard layout on OSX and &#960; ™ £ &#8721; á ¥ ö ô å ß ƒ © &#8734; &#8800; &#8776; &#8747; ° — ± ¿  are a handful of useful characters that can be found with some combination of shift, alt, [something else] in OSX's keyboard layout. That's probably the one feature that I actually miss from OSX to Ubuntu, other than that I vastly prefer Ubuntu. Anyways, after I'm back in Ubuntu I'll look at the things you mentioned and let you know how it went.

---

### Post by y@w on 2008-08-21
Ok, I used to have issues getting my linux machine on my school's network. I had to run a different version of dhcp to make it work (dhcpcd maybe?). I'd check out the settings that the dhcp server hands out in OSX and set them staticly in Ubuntu. I fought the same thing at my school with them not wanting to support anything besides Microsoft...

---

### Post by spencercarran on 2008-08-22
> **y@w said:**
> Ok, I used to have issues getting my linux machine on my school's network. I had to run a different version of dhcp to make it work (dhcpcd maybe?). I'd check out the settings that the dhcp server hands out in OSX and set them staticly in Ubuntu. I fought the same thing at my school with them not wanting to support anything besides Microsoft...

OK... I'm still really new to Linux, so do you think you could explain in more detail please?

My school supports Macs- even peddles them quite enthusiastically. They just don't like Linux.

---

### Post by y@w on 2008-08-22
Well.. the major problem was that the machine wasn't getting an address reliably and sometimes it wouldn't receive DNS servers when using the out-of-the-box dhcp client that came with Ubuntu. I was fairly new to Linux at the time and it's been a little while so this might not work exactly as I describe, but it should give you a little bit of road to run on at least. I had to kill all dhcp processes that were running with something like:
```
ps aux | grep dhcp
```

You should get a process that comes back called dhclient3 (at least that's what it gives me on my box). You'll want to kill that process:
```
killall dhclient3
```

Or you can kill it using the pid. Then install dhcpcd:
```
sudo apt-get install dhcpcd
```

Then just restart your interfaces:
```
sudo /etc/init.d/networking restart
```

Again, not sure if this is even in the right direction.. but I did have some problems with dhcp on the network kinda like that and had to switch. I'd probably be more tempted to start with switching to using a static entry that matches what your OS X machine was given via dhcp first. You can configure that all through the System menu on Ubuntu.. I'm on my MacBook at the moment so don't have access to a Ubuntu desktop to see.

---

