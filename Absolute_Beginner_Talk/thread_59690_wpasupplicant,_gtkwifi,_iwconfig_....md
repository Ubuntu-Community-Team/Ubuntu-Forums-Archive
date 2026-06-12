---
title: "wpasupplicant, gtkwifi, iwconfig ... ???"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by sneax on 2005-08-25
Hello,
I know all these programs but I don't fully understand what they are doing.
- wpasupplicant creates wpa support, can only be configurated by config
- gtkwifi shows which AP you connected too with some handy info
- iwconfig shows info about wireless devices in your computer in cmd prompt

now my question(s):
How are they all related to each other? I understand wpasupplicant actualy is the main program that says the drivers and wireless card what to do and how to connect. Do I need any program then addiontal to wpasupplicant?

Or is it like this: wpasupplicant configures your stuff and holds the encryption logic and stuff. Iwconfig actualy holds the radio connection (and sends through whatever data wpasupplicant gives) and gtawifi is a sort of small front end for iwconfig?

I'm having trouble understanding how those programs work together which makes it very dificult to configure my system correctly too.

Now don't point me to the howto's, I've read them, they don't answer my question. Thanks in advance  \\:D/

---

### Post by npaladin2000 on 2005-08-25
Actually, you're having a lot of truuble, which is a lot more than you think you have. ;)  But that's OK, I shall explain.


iwconfig is the Linux Wireless Tools (Ok it's only a part of it, but it's the main part).  This is the main interface (basically) to controlling the WLAN card's functions, including SSID, WEP encryption and type, etc.  

GTKWifi is a frontend to iwconfig and some of the other Linux Wireless Tools.  It does the same job, but through a GUI rather than CLI.

wpa_supplicant enables advanced wireless encryption.  If you've heard about WPA-PSK, WPA-RADIUS, AES, TKIP, or any of that, that stuff requires wpa support, and therefore wpa_supplicant. There currently is no GUI frontend to wpa_supplicant, but the CLI is OK (wpa_cli).  You're best off directly editing the config file, and using wpa_cli to get status. 

NetworkManager and it's associated daemon are supposed to have preliminary WPA support, but it won't work on Ubuntu, so I don't know if it's direct or through wpa_suplicant (probably the latter). 

I was considering rewriting/forking GTKWifi to work as a GUI frontend to wpa_supplicant (since I'm learning Python and all) but the latest posted source is a bit outdated, and I can't tell if Network Manager has beaten me to the punch. ;)  But wpa_supplicant doesn't like managing regualr WEP encryption, so it's going to be harder than I thought anyway.....besides, my new Aethros WLAN card can't handle scanning and maintaining the connection at the same time. :(

---

### Post by sneax on 2005-08-25
Ok. So actualy I have to change between wpa_supplicanat and gtkwifi+iwconfig to change between wpa and wep?

I have them both on my system and have no idea which on is in charge! Or am I still missing the point? ;)

BTW: I see there is a lot of easy work still to be done in linux, for the most part actualy the main thing that linux is missing for the desktop is frontends frontends and more frontends. I'm studying informatics at uni, and we are learning to program java, and will learn much more languages probably. I think once I'm good enough at it, I'll make ubuntu an uber desktop  linux system by contributing frontends for everything that could need one ;)

---

### Post by npaladin2000 on 2005-08-25
[QUOTE=sneax]Ok. So actualy I have to change between wpa_supplicanat and gtkwifi+iwconfig to change between wpa and wep?

I have them both on my system and have no idea which on is in charge! Or am I still missing the point? ;)

BTW: I see there is a lot of easy work still to be done in linux, for the most part actualy the main thing that linux is missing for the desktop is frontends frontends and more frontends. I'm studying informatics at uni, and we are learning to program java, and will learn much more languages probably. I think once I'm good enough at it, I'll make ubuntu an uber desktop  linux system by contributing frontends for everything that could need one ;)[/QUOTE]

Not in java.  PLEASE not in Java.  On top of it not being a preferred language in Linux, it's a total bear.  Plus the fact that you have to make sure it works with the GCC JavaVM, since most distros do NOT come with the Sun VM (Heck, even WINDOZE doesn't).   Plus it kinda sucks interfacing with either Qt or GTK2. 

I'm learning Python now (well, first I'm catching up on my sleep and attempting to arrange finishing college) and it seems pretty easy to pick up after Java (which I learned as well). 

Anyway, back to WEP/WPA....basicallly, if wpa_supplicant isn't running, iwconfig is handling things. If the supplicant IS running then it's handling your encryption (it's supposed to handle WEP too).  Depending on how the supplicant is configured it might be handling AP scanning too...that's optional.

I highly recommend installing wpa_suppplicant (it's not enabled by default) and reading the example config file that gets installed with it, to get a better idea of what it does.

---

### Post by sneax on 2005-08-26
Thank you for your help, I now fully understand what all those parts are doing ;) I'm already running wpa_supplicant and already made a config file (with 2 networks) but I wasn't sure who was doing the WEP encryption etc... now I know wpasupp is doing it all. Gtawifi is good to see which networks are in the neiborhood then edit wpasupplicant.conf (I have a link to it on my desktop). It's not the best but it's ok :)

For the programming part: yes I know Java isn't good because it requires the Java VM - but it's my first OO language so I guess when I know the big basics of Java I can learn most languages without too much trouble. I hope in about a year or two that there are still things left to program so I can contribute my share to the open source world too  :smile:

---

### Post by npaladin2000 on 2005-08-26
Just be aware that it might not be well recieved or wanted if it's in Java, since it's not an open-standard language. Basically, you'll have to make your apps depend on the gjj Java VM....which supports a SUBSET of the SUN Java VM features.  Forcing dependence on the SUN Java VM is near enough impossible.

---

