---
title: "can use gaim??"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-07-29
ok, i can surf the internet at my normal speed but i cant use gaim. it just keeps connecting and then it times out. i would download aim, but i dont know how to install things. i have been trying to for the past 2 hours with no luck. can someone help me pleas?

---

### Post by GavinX on 2005-07-29
Which version of GAIM are you using? My suggestion is that you upgrade to the latest version. Also, is your system firewalled? If so, you may need to do some reconfiguration of the firewall.

---

### Post by servvs on 2005-07-29
[QUOTE=GavinX]Which version of GAIM are you using? My suggestion is that you upgrade to the latest version. Also, is your system firewalled? If so, you may need to do some reconfiguration of the firewall.[/QUOTE]
 the thing is, i dont know how to install things. ive tried over and over again. and i dont have a fw and its not my router either, cuz i unplugged it for now.

---

### Post by trivialpackets on 2005-07-29
[QUOTE=servvs]the thing is, i dont know how to install things. ive tried over and over again. and i dont have a fw and its not my router either, cuz i unplugged it for now.[/QUOTE]
 Have you seen the ubuntuguide.org.  It gives a decent list of repositories that can be enabled, then from there, use synaptic, either from the menu, or CLI sudo synaptic mark all upgrades, and go to town....  Get to know synaptic, it's a great piece of software for locating new and upgrading old software.

---

### Post by GavinX on 2005-07-29
[QUOTE=eric.proctor]Have you seen the ubuntuguide.org.  It gives a decent list of repositories that can be enabled, then from there, use synaptic, either from the menu, or CLI sudo synaptic mark all upgrades, and go to town....  Get to know synaptic, it's a great piece of software for locating new and upgrading old software.[/QUOTE]
I second the motion. Great suggestion. :)

---

### Post by arundhati_bakshi on 2005-07-29
[QUOTE=servvs]the thing is, i dont know how to install things. ive tried over and over again. and i dont have a fw and its not my router either, cuz i unplugged it for now.[/QUOTE]

Try this:

apt-get install gaim

And that shoukd install the newest version of gaim for you.

---

### Post by bored2k on 2005-07-29
1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
3. sudo apt-get update
4. sudo apt-get install gaim --force-yes -y
(Optional)
[COLOR=RoyalBlue]* Upgrade Mozilla Firefox[/COLOR]
5. sudo apt-get install mozilla-firefox --force-yes -y
[COLOR=DarkRed]* Upgrade entire system[/COLOR]
6. sudo apt-get dist-upgrade --force-yes -y
[COLOR=RoyalBlue]* Multimedia codecs[/COLOR] ([COLOR=Indigo]divx, mp3, wmv, etc[/COLOR])
7. sudo apt-get install w32codecs gstreamer0.8-plugins totem-xine --force-yes -y

[http://ubuntuguide.org/#add-onapplications](http://ubuntuguide.org/#add-onapplications)

---

