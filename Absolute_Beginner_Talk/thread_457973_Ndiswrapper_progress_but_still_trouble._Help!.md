---
title: "Ndiswrapper progress but still trouble. Help!"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by seismicmike on 2007-05-29
OOOOKAY!!! Here's some interesting times... I tried out MEPIS for a bit which comes pre-installed with ndiswrapper (something ubuntu propper should consider!) and it was nice b/c they have this network assistant that did everything (EVERYTHING) automatically - and it had a bunch of drivers pre-installed.... Well.. I tried to do some upgrades and screwed the distro up (I changed all repositories to feisty and said mark all upgrades... I guess for some reason it decided to install Korean fonts (cause i'm in Korea) and it didn't work right and so all I had were boxes instead of text) and got to a point where I knew I had to re-install so I decided to give ubuntu another try.... so I grabbed the wireless drivers that Mepis came with (off the live CD) and tried them in ubuntu and LOW AND BEHOLD THEY WORK!!! (to some extent)

I used synaptic to install ndiswrapper along with ndgk (or whatever it's called - the gui) And I installed the driver and it said "driver installed, hardware present"

Now unlike times before where I've gotten this far, the device actually appears in the network dialogue System > Administration > Networking BUT It won't connect to the network!!!!!

Does anyone know where to go from here? I've tried Wireless Assistant (wlassistant). I've tried K Network Manger... I've tried configuring the card by DHCP and I've tried using a static address - no network. iwconfig sees the card, but again I can't get it to connect to the network. I've edited the /etc/network/interfaces file manually - no dice.

Does anyone have any suggestions???? I see the light at the end of the tunnel! Please help me out!!!

---

### Post by SpacedMonkey on 2007-06-02
I'm trying to get wireless assistant installed in the first place! i'm playing the follow the bounding dependency game. Seems like every thing I need to install requires just one more other package (ad infinitum) just to install ONE app. This is getting disheartening.

It would be easy to keep downloading these things if I had an internet connection on the ubuntu box...

---

