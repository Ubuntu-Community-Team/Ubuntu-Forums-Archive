---
title: "Wireless problems up the wazoo! (wmp54g)"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by satyrical on 2006-12-11
Alright .. so here's my deal: I consider myself a windows expert so this is really getting on my nerves that I can't hash this out on my own... 

I have tried multiple times to get my Linksys WMP54G to work inside Ubuntu (Edgy) for the better part of 4 days now. I have downloaded and installed ndiswrapper, ndisgtk, along with a few "proven to work" versions of the drivers for my card. 
The PCI ID is... 14e4:4320 (rev 03)

The instructions I found from the Ndiswrapper Wiki said to blacklist the original drivers bcm43xx, which I did, and then tried to proceed on to installing the new drivers. This all seems to go just fine, however if I look in System/Networking there is no Wireless Connection present, only wired. If I un-blacklist those original drivers, I get my Wireless Connection back in Networking, however in iwconfig my device shows up as eth1 instead of wlan0 ...

Does anybody have any soddid clue as to what is going on with my machine? I appreciate any and all help in advance, thanks again and you forum junkies are literally a god-send, thank you.
-C.Hunt

---

### Post by koolkid64us on 2006-12-11
Well, I was in the SAME situation as you pretty much, except I have a Netgear WG111 v.2 USB dongle (Prism2 Chipset).  What I did was revert back to version 6.06 LTS.  You really should wait for more responses than doing what I did first, you may get a solution ;)

---

### Post by satyrical on 2006-12-11
Reverting to a previous version of Ubuntu solved your problem? How is that possible? 

Did you just use one of the preload drivers or did you still have to end up using ndiswrapper with one of the 3rd party drivers?

---

### Post by Hendrixski on 2006-12-11
it may be a faulty card?  do you have it under warranty?

---

### Post by satyrical on 2006-12-11
Here is the tricky part- I am dual booting Windows XP SP2 with the exact same wireless card on the same network- works fine.

-The real question of the hour is why does it keep registering in iwconfig as eth1 instead of wlan0 ?

---

### Post by CoolHand on 2006-12-11
There are a couple of things that could be the problem.  I use a broadcom card as well under ndiswrapper.  The reason reverting to 6.06 probably worked for the other user is that there is some mixup in the loading of the ndiswrapper-utils under edgy.  That doesn't mean it won't work.  You probably have the same problem.  I forget which one loaded when I installed ndiswrapper but I think it was ndiswrapper-utils-1.1 and to get it to work I had to use apt-get to install ndiswrapper-utils-1.8.  It may be the other way around though.  Once I did that I could get the driver to install properly and it came right up.  There was another thread where I found that answer.  If what I just said isn't enough do a search and you should find more answers on the ndiswrapper glitch.  You don't really need the gui to set it up as it is only 3 commands.  Here is my whole setup to get the driver loaded for example:
```
ndiswrapper -i netcbg54.inf
modprobe ndiswrapper
ndiswrapper -m

```

As for showing up as eth1...I had that problem on my previous install.  Make sure under /etc/modprobe.d you have the file ndiswrapper with the following contents:
```
options ndiswrapper if_name=wlan0
alias wlan0 ndiswrapper
```
I think that fixed it for me to force it to wlan0 every time.  If that doesn't help I'll dig through my notes some more.

---

### Post by satyrical on 2006-12-11
I'll give that a whirl.. is there any reason I should have to blacklist the original drivers? bcm4xx?

As per the Ndiswrapper wiki instructions ? 

Also, I've got the 1.8 utils loaded already. Any other ideas?

---

### Post by CoolHand on 2006-12-11
> **satyrical said:**
> I'll give that a whirl.. is there any reason I should have to blacklist the original drivers? bcm4xx?

As per the Ndiswrapper wiki instructions ?
Yes you need to blacklist them.  On reboot the system will try to load the native driver first and when ndiswrapper tries to load it's driver there will be a conflict because they are both trying to run the same device.  That may be an over-simplification but that is basically what happens if you don't blacklist it.

Do you have the 1.1 utils loaded?  I can't remember which was the one needed.  The post I read said to remove one and add the other but that is not what I did.  My card started working after I added the missing one and I never removed the other.  I vaguely remember having to call version 1.8 explicitly to install the driver or something like that but I'm not sure.  Sorry I didn't keep better notes.

---

### Post by trav5 on 2006-12-11
I got mine to work with this [http://www.ubuntuforums.org/showthread.php?t=277037&highlight=ndiswrapper+wpc54glink](http://www.ubuntuforums.org/showthread.php?t=277037&highlight=ndiswrapper+wpc54glink) and this link which is in that link [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809) . I still have mine running on eth1 and have no problems. The big hurdle for me was not unplugging the ethernet cable

---

### Post by satyrical on 2006-12-11
> Do you have the 1.1 utils loaded? I can't remember which was the one needed. The post I read said to remove one and add the other but that is not what I did. My card started working after I added the missing one and I never removed the other. I vaguely remember having to call version 1.8 explicitly to install the driver or something like that but I'm not sure. Sorry I didn't keep better notes.

As far as I know I have 1.1, 1.5, and 1.8 all installed.

---

### Post by satyrical on 2006-12-11
Unfortunately, it seems, just as I expected, that as soon as I blacklisted the bcm43xx drivers, the wireless connection disappears in Networking and iwconfig no longer shows a connected wireless adapter. Device Manager still sees it however.
What am I doing wrong here?

I just don't get it... I blacklist the bcm4xx drivers, I install new drivers with ndiswrapper, it says installed in ndiswrapper -l but, there are NO wireless devices in System/Administration/Networking and iwconfig doesn't show any connected devices. WTF!?

---

### Post by satyrical on 2006-12-11
Bump.. dear god help me before my fist ends up through my screen.

---

### Post by igknighted on 2006-12-11
please don't bump after an hour, you should wait about a day or so before a bump...

anyways, on to more important things... what is your precise output for the following command: 'sudo ndiswrapper -l'

---

### Post by CoolHand on 2006-12-11
> **satyrical said:**
> Unfortunately, it seems, just as I expected, that as soon as I blacklisted the bcm43xx drivers, the wireless connection disappears in Networking and iwconfig no longer shows a connected wireless adapter. Device Manager still sees it however.
What am I doing wrong here?

I just don't get it... I blacklist the bcm4xx drivers, I install new drivers with ndiswrapper, it says installed in ndiswrapper -l but, there are NO wireless devices in System/Administration/Networking and iwconfig doesn't show any connected devices. WTF!?

Are you loading ndiswrapper after you blacklist the native driver?  Do an lsmod and look at the loaded modules for ndiswrapper.  If it is not present do sudo modprobe ndiswrapper.  Also do an ndiswrapper -l and show me that output so you can see that the proper driver is installed.  If ndiswrapper is not loading on boot try running sudo ndiswrapper -m to write the files to load the module on boot.

---

### Post by satyrical on 2006-12-13
Ok- Ladies and gentlemen- after a long a hard-fought battle- I caved an went back to 6.06 (Dapper Drake) and after blacklisting the original drivers, loading the same drivers I had tried a million times with ndiswrapper, Dapper is working fine- in fact I am posting this message in Ubuntu as we speak. W00t.

Thanks everyone for all the help.

Bottom line- Linksys WMP54G PCI ID - 14e4:4320 (rev 03) works only with 6.06 (Dapper) with Version 2.0 drivers from the Linksys website. Hope this helps anybody else who runs into this problem.

---

