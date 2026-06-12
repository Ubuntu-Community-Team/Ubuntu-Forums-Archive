---
title: "Attack of the giant terminal as Network Manager hides"
date: 2012-08-02
forum: Apple Hardware Users
---

### Post by Bucky Ball on 2012-08-02
Hi all,

As the title suggests. I can't remember doing anything  but was fooling around with Unison over the home network previously,  although nothing appeared odd.
 
Previous to that, Network  Manager, which would appear pretty much when the desktop did, started to  delay its appearance for about 30-45 seconds. When it eventually  appeared whatever I'm doing closes, not crash, just close, and an empty  terminal pops up! (If I don't open a terminal before this point it is a fullscreen one: see below).

So, now on reboot, when I get to the desktop, the first terminal I open is fullscreen size (I never use them that big),  empty. This sometimes just appears by itself. I close that and once the network manager appears everything  seems normal. But this boot is not. Any other terminal I open after that is normal size; about 1/4 or the screen size. 

Any ideas what's happening?  It seems to be throwing a lot of Bluetooth stuff in the initial dmesg  after boot, but I'm not using Bluetooth and have it switched off for  launching at start-up. 

Any help gratefully appreciated. Will add more info later ... Cheers. ;)

---

### Post by Bucky Ball on 2012-08-02
Narrowed it down a bit. Managed to get rid of the giant terminal. Now I open a terminal before Network Manager and it's normal size. When Network Manager does eventually open it shuts that terminal and briefly opens another then closes it again. Then I'm online and all looks good, behaves normally. 

The other really strange thing is that my logout/restart/shutdown button has disappeared. There was a strange episode where I had two icons for everything in the top taskbar and tried deleting and moving things to fix. Probably just made things worse. 

Let me know if more info required ...

---

### Post by Bucky Ball on 2012-08-03
Okay, the journey continues, I have a couple of ideas ...

Not fullscreen terminal, but regular size one comes up after the delayed Network Manager (by itself). It no longer disappears, just stays there until I close it. When I logout, I get the silhouette of *the same terminal *I had at boot, nothing in it, just a grey square in *the* *same spot the boot one was*. 

Something that started with me in the Windows days is I always close all programs before shutting down. But, I remember shutting down in a hurry around the time these issues started happening, and things were open at the time. My theory? I reckon the 'save session for next time' box was ticked on the logout window. 

Something lingers. I have a feeling there is something happening in the background, not sure which log to start with. Nothing unusual shows in 'top'.

The NManager delay is boring and the random terminal a mystery. But I think I may have figured out the NM problem. Out of curiousity, I had a look in /etc/network/interfaces, and discovered:

```
auto lo
iface lo inet loopback
```That's it. I have static IPs all round so I have no idea what happened to the configuration in there. Haven't even looked there for months. There's no wlan0 entry for a start. Guess that could be causing the delay. Could someone paste a copy of their /interfaces file (if they have wireless) so I can use that as a template to rebuild mine? Save me digging, I'm pushed for time ... but aren't we all! 

The only good news is, as I say, once the palaver is over it seems to be running ok. But I don't trust it when there's something lurking under the bonnet ...

All clues welcome and tnx in advance ... ;)

---

### Post by steeldriver on 2012-08-03
The /etc/network/interfaces file is used by the older networking service (aka 'ifupdown') - it's completely normal for it to have only the lo definition if you're using NetworkManager for all your interfaces (in fact that's the default for current desktop installations) - your wireless interface definitions should be in /etc/NetworkManager/system-connections (if they are system-wide) or iirc buried somewhere in the gnome .config tree if they are user-connections

I have no idea what your other issues are - maybe create a new user account and see if that does the same - this would narrow it down a bit i.e. whether your whole desktop environment is messed up or just something in your current user config

---

### Post by Bucky Ball on 2012-08-03
Thanks for your input. Fixed ... not. I installed 12.04 LTS and it 'just works'. I am a bit stunned, shocked, and amazed things could go that wrong on an old, previously rock solid, LTS release without me having done anything radically tweakerish. I wasn't doing any system tweaking as I need that install to be rock solid so don't. 

Oh, well. Never know now. Not solved but 'problem resolved', an insidious mystery, case closed. I love Linux but things like this really make me wonder ...

---

