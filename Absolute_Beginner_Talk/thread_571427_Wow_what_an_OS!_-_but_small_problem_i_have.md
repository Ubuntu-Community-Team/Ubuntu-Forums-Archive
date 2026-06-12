---
title: "Wow what an OS! - but small problem i have"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by madds007 on 2007-10-09
Well I switched from WinXP at the weekend, and am running Gutsy Beta on my System, what an OS, but a small problem, I have Logitech USB Headphone with mic for skype etc, the problem I have is when using Amarok the sound will not route through the headphones only through the desk speakers, banchee & rhythmbox i dont have a prob with, any suggestions?

Andy

---

### Post by WebSiteGuru on 2007-10-09
I just upgraded myself to Gutsy, so I am still trying to figure everything out.

I have not actually use Amarok, but have you look and see if there is the configuration for Amarok? Some of the software, as I understand, you can go to the configuration and change you option to have the sound output to other devices.

---

### Post by -Zeus- on 2007-10-09
This might help... I have a Plantronics USB headset and use it in TeamSpeak.  I found that in TeamSpeak, I can manually set the sound card from /dev/dsp (default) to /dev/dsp1 (my headset).  maybe there is something like that?

---

### Post by goodboyCerberus on 2007-10-09
Good luck in finding a solution, however I would suggest waiting for the official release. Don't expect everything to work in a beta. ;-)

You can file bugs [here]("https://launchpad.net/ubuntu/+filebug"), but you have to register via email verification.

---

### Post by madds007 on 2007-10-10
Yeah I know its a beta, thats why, I'm not pushing on this as urgent, but will be nice when it does

---

### Post by Circus-Killer on 2007-10-10
you mentioned you are using amarok? does that mean you are using kubuntu?

if not, and you are using normal ubuntu, then just take a look under the main menu under "System -> Preferences -> Sound".
There you will find options for sound output. If everything is fine under there, then you will have to look at output settings within amarok, i'm not sure about those.

if you are using amarok under ubuntu/gnome, you might want to try out exaile, as it is designed to be similar to amarok, but written for gtk instead of qt.

hope you have better luck, but as someone else said, dont ever expect everything to be working in the beta release. rather wait till final release day.

---

### Post by 3rdalbum on 2007-10-10
That the sound works fine in Exaile and Rhythmbox (both Gnome programs) suggests that ARTS (KDE's sound system) might be the problem. Try installing the "kcontrol" package, then starting it up:

```
kcontrol
```

And check the sound settings there.

---

