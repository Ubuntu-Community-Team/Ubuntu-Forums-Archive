---
title: "Wireless all messed up"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-28
Well, my wireless connection kept kicking me off.  I did some research and found it was a common problem, someone recommended using kwlan since I already had the kubuntu libs. 
I know when I installed kwlan it took out network manager and another package

Right off the bat I could not get kwlan to connect to any kind of secure network, when I got home it started to complain about wpa_supplicant and would'nt let me get to ANY network

now I just want my old configuration back

I used network-manager-gnome, wpa_supplicant(which I think is messed up now) and I think another package along with network manager

Can someone point me to a how to on getting the wireless up again, I looked but cant find the one I used when I got the lappy up and running

---

### Post by handaxe on 2007-03-28
In synaptic you can reselect those programmes such as wpa_supplicant and NetworkManager and in the "package" menu, choose  re-installation for proggies that are still installed. You probably know this... but maybe I misunderstand you...? If the missing programme was a dependency then that you be OK. If not, then it was not crucial

You can also try an alternative network connection manager known as Wicd.  Good on different encryption types, and makes WPA partic easy
Some folk have found success with it. Yes, I know you got into trouble doing that before :)

Wicd also uses wpa_supplicant.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by entering /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper) as a startup proggie (I am a long term Gnomer and KDE is a mystery to me...)

See how this goes.

HA

---

### Post by charles.g.moore on 2007-03-28
I got my initial set up back by just removing all networking packages and then reinstalling
Thanks for the help...
I will do some more research into alternate wifi gui tools before grabbing one

---

