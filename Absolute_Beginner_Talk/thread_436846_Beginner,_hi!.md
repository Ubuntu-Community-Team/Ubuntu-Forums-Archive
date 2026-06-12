---
title: "Beginner, hi!"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Lhademmor on 2007-05-08
Hello. I am what you would call a beginner to Ubuntu. I have a huge interest in Ubuntu and hope that someday I may learn enough Python to actually contribute to the project.

I've got a 1.6 GHz laptop (ThinkPad) and a 2.4 GHz stationary. Unfortunately, I cannot use Ubuntu on the stationary because Ubuntu won't play the sound (Creative X-Fi sound card) :(
The laptop has XP/Feisty dual-boot, but it's not working out very well... I accidentaly installed Kubuntu-desktop-package on Ubuntu, and it installed a bunch of stuff that I've desperately tried to remove, because it made the laptop slow as hell...

Also, the wireless network card has a very poor performance compared to when used under XP. AND my school is blocking me from using the network connection while on Ubuntu, because they want to force us to use XP Professional :mad: 

Luckily, I've only got four days left of school and after that I'm out. I'm thinking of formatting the laptop completely and only install Ubuntu, but I've been thinking...
I mainly use it for:
*IM (MSNm)
*Internet (Firefox)
*IRC (Firefox-ChatZilla)
*P2P (Gnutella/BitTorrent)
*Danish-English dictionaries

The latter is unfortunately only available to Windows it seems :( , but apart from that I guess I should be able to use Ubuntu?
Also, I'll be studying to "Datamatician" (really the educational programme of Advanced Computer Studies) next year, so I reckon Ubuntu could be a good choice due to it's openness?

And finally, any good links to a programming newbie who would want to one day be able to participate in the development of Ubuntu-modules?

That was a bunch
Thanks

---

### Post by bapoumba on 2007-05-08
Thread moved to "Absolute Beginner Talk" support forum.

---

### Post by starcraft.man on 2007-05-08
If you installed the kubuntu-desktop by accident, you can always just do

```
sudo aptitude remove kubuntu-desktop
```... it should all be deleted.

As for the wireless stuff, ya, wireless is still a bit of a problem. Have a look at NDISwrapper, usually you can find a good fix from them (linksys though seems to be the worst supported, not Ubuntu's fault I don't think). 

Lastly, as to the school... do you mean they told you you can't use your Ubuntu pc on the network? Or that they have set up the connection so that you can't. If so, I'd say its just another example of uninformed people being in charge of the network. Download the Linsta theme or XP theme from gnomelook and skin it so it looks like windows (just for when your in school) :)

---

### Post by houstonbofh on 2007-05-08
How to totally remove kubuntu;
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

What WiFi card, and how is the school blocking you?

---

### Post by starcraft.man on 2007-05-08
> **houstonbofh said:**
> How to totally remove kubuntu;
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

What WiFi card, and how is the school blocking you?

Ya, I should have asked... broadcom/linksys are so problematic it seems with Ubuntu >.> I do doubt however that the school actively has a process for scanning to see your running Ubuntu, that would be very extreme... not to mention stupid. If it is just something they don't like, get the XP skin from gnome look to trick em, and if they ask you why your task bars are different, just say you've installed custom hacks :)

---

### Post by Lhademmor on 2007-05-08
> **houstonbofh said:**
> How to totally remove kubuntu;
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

What WiFi card, and how is the school blocking you?

I can't remember the card.. I'll have to check on that.
As for blocking, they probably blocked me because on the school we have to use laptop-names like "99LYAxx" (xx=numbers) AND be on the "workgroup" (or whatever it's called - the thing selected beneath PC-name) called "JOHANNESSKOLEN".

Unfortunately, Ubuntu keeps defaulting the workgroup to blank. I dunno why. Also, maybe I could get them to unblock me because I have dualboot with Windows.

The IT-guy has already stated that we're only supposed to run XP. Probably because otherwise he would find support too hard...

---

### Post by houstonbofh on 2007-05-09
Put XP in a small VM and have it connect through your IP.  Instan't sucess. :D

---

