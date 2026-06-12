---
title: "Is Feisty worth it right now"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-04-11
So i have to reformat my machine due to an un-cureable kde issue... I was running edgy and am currently downloading Feisty beta... was wondering a few things:

Is the switch worth it this close to official release... are there any expected major bugs with only a little over a week left to go?

I've noticed a lot of issues with recent updates and nvidia drivers... is nvidia-glx gonna be easier or harder to deal with than edgy... i could never get nvidia-glx to work right before and always resorted to manual install of package from nvidia's site?

Is there a list anywhere of third party repositories for feisty or is it to soon... my cureent sources.list is composed of repos such as the plf, seveas, trevinos, bleeding edge wine. Is there even a need for the third party repos or has most stuff made it to the official repos with feisty?

Speaking of wine... i noticed that the official repo version is a version or two behind the current version... can i simply replace edgy with feisty in the budgetdedicated repo to get bleeding edge on feisty? Im trying to make the full switch from cedega to wine but its just not gonna happen if i cant get the latest wine, specially with cedega 6 coming out in a few days.

My current sources.list contains edgy repos for up to date kubuntu/kde releases from kubuntu.org... is there a feisty repo for that yet, or once again, should all that be coverd in the official ubuntu repo

I think that about covers it since i have no desire to even install beryl again.

any other performance experiences or recomendations welcome... im looking forward to the upgrade

---

### Post by igknighted on 2007-04-11
> **Nythain said:**
> So i have to reformat my machine due to an un-cureable kde issue... I was running edgy and am currently downloading Feisty beta... was wondering a few things:

Is the switch worth it this close to official release... are there any expected major bugs with only a little over a week left to go?

I've noticed a lot of issues with recent updates and nvidia drivers... is nvidia-glx gonna be easier or harder to deal with than edgy... i could never get nvidia-glx to work right before and always resorted to manual install of package from nvidia's site?

Is there a list anywhere of third party repositories for feisty or is it to soon... my cureent sources.list is composed of repos such as the plf, seveas, trevinos, bleeding edge wine. Is there even a need for the third party repos or has most stuff made it to the official repos with feisty?

Speaking of wine... i noticed that the official repo version is a version or two behind the current version... can i simply replace edgy with feisty in the budgetdedicated repo to get bleeding edge on feisty? Im trying to make the full switch from cedega to wine but its just not gonna happen if i cant get the latest wine, specially with cedega 6 coming out in a few days.

My current sources.list contains edgy repos for up to date kubuntu/kde releases from kubuntu.org... is there a feisty repo for that yet, or once again, should all that be coverd in the official ubuntu repo

I think that about covers it since i have no desire to even install beryl again.

any other performance experiences or recomendations welcome... im looking forward to the upgrade

Well, I think that given the choice between doing a fresh edgy install only to upgrade in a few weeks and just using the beta, I would say go with the beta.  It is certainly not without bugs, as I have found many, but they are workable.

Nvidia-glx is now the newest version in feisty, so you get the full compositing effects.  If you do want to give beryl a go again, its easy as pie and mostly stable.  In fact, compiz is installed by default, so you could run it as soon as you install if you like (see the desktop effects program).

I don't know if these third party repos are available for feisty yet.  I doubt most of these programs have made it into the official repo's though, so you might want to check that out.

Wine should be the newest version (or at least newest as of Januaryish, whever the freeze was).

Give feisty a shot, the worst thing that happens since you're reformatting anyway) is you decide to wait.

---

### Post by LookTJ on 2007-04-11
Depends on what you're looking for. I hadn't had a problem at all yet.

Give it a go and see for yourself :)

---

### Post by xopher on 2007-04-11
It's been working without any hitches here too, for about a month and a half ;)

---

### Post by IndyBob on 2007-04-11
I tried an update from Edgy to Feisty and it bombed, so then I used the live CD and did a clean install.  I liked several things in Feisty, but I kept getting  a boot error of acpi force required and then everything would lock up and it would take two or three boots to finally load.  I would wait for the final release of Feisty before I tried it yet.  I know I am going to wait at least a month before I try it again as I re-installed Edgy.

---

### Post by ginnie6 on 2007-04-11
I tried the upgrade too and had major problems with my nvidia card. Couldn't get beryl or compiz to work. So I went back to Edgy where everything works perfectly. I'll probably wait a month or so before I upgrade. I'm still new to Ubuntu but so far i love it.

---

### Post by bodhi.zazen on 2007-04-11
If the Feisty live CD works, I'd say go for it.

I've been on feisty sicne herd 1 and had only minor problems.

FYI there is an entire forum on Feisty : [http://ubuntuforums.org/forumdisplay.php?f=179](http://ubuntuforums.org/forumdisplay.php?f=179)

---

### Post by aktiwers on 2007-04-11
Just installed Feisty..  and wow its worth it. 
This is really an improvement! It even installed my nVidia drivers automatically.. All I had to say was it was ok.

---

### Post by macogw on 2007-04-11
Feisty's great for laptop users by default now because wireless roaming is now no-work-involved (okay, WPA requires erasing a bunch of lines from /etc/network/interfaces, but that's how it's always been as far as I can figure out).  Like they said, desktop effects are installed by default, though you'd want to apt-get gnome-compiz-manager to have more effects available to play with on it.  I don't see any *major* bugs left.  There's a broken driver for internal Texas Intruments card readers (I think this is in the vanilla kernel too, not an Ubuntu thing), but someone made a little workaround to get that going.  The network manager is, as of this morning, lying and saying it's disconnected even while I'm using the internet to type this, so I find that funny.  Umm...oh, gdm takes a few seconds longer than it should to load the GNOME DE,  but kdm loads GNOME fast, so go figure on that.  And imlib1 is still broken, keeping gnome-breakout from being a playable game (I believe this also has a workaround).  Xchat-gnome is broken, but it's an upstream problem, so use Gaim or regular Xchat instead.  Nothing's  "show-stopper."  They're all minor annoyances, and most have a workaround that takes about 5 seconds.

---

### Post by jputman01 on 2007-04-11
i think it is worth it, i have been using it for about a month. not to say i haven't had any issues but i have fixed almost everything that has gone wrong. nvidia is working fine, wireless is fine, im running 64bit version and have 32bit opera running flash and java just fine, desktop effects works great(no crashing). everthing else worked out of the box. I say go with the beta! im very happy with it

---

### Post by gerrymoth on 2007-04-11
> **macogw said:**
> Feisty's great for laptop users by default now because wireless roaming is now no-work-involved (okay, WPA requires erasing a bunch of lines from /etc/network/interfaces, but that's how it's always been as far as I can figure out).  Like they said, desktop effects are installed by default, though you'd want to apt-get gnome-compiz-manager to have more effects available to play with on it.  I don't see any *major* bugs left.  There's a broken driver for internal Texas Intruments card readers (I think this is in the vanilla kernel too, not an Ubuntu thing), but someone made a little workaround to get that going.  The network manager is, as of this morning, lying and saying it's disconnected even while I'm using the internet to type this, so I find that funny.  Umm...oh, gdm takes a few seconds longer than it should to load the GNOME DE,  but kdm loads GNOME fast, so go figure on that.  And imlib1 is still broken, keeping gnome-breakout from being a playable game (I believe this also has a workaround).  Xchat-gnome is broken, but it's an upstream problem, so use Gaim or regular Xchat instead.  Nothing's  "show-stopper."  They're all minor annoyances, and most have a workaround that takes about 5 seconds.

I upgraded from Edgy 6.10 to Feisty 7.04 because I was having problems geting WPA & WEP to work on my ACER 2428 laptop, to the point I was ready to give up on Ubuntu, but after installing Feisty 7.04 I can connect to both WEP and WPA connection without changing or deleting anything.
After installation the Network Manager found all available connections, I put in the SSID and Password and away I went surfing the web.

Was up and running with internet, email and chat straight out of the box. I love Gaim, still to export my contacts to Evolution and always used Firefox in WinXP. 

I've sorted out after reading the easy to use Ubuntu Guides how to mount drives, setup Sipgate using Ekiga, DVD playback, DVD burning, DVD ripping, playing mp3's and adding/deleting music in my iPOD Mini. 

All I need to sort out is syncing to my Nokia N73 and I may consider reformating the windows partition with WinXp on it.

Ubuntu Rocks.:guitar:

---

### Post by macogw on 2007-04-11
> **gerrymoth said:**
> I upgraded from Edgy 6.10 to Feisty 7.04 because I was having problems geting WPA & WEP to work on my ACER 2428 laptop, to the point I was ready to give up on Ubuntu, but after installing Feisty 7.04 I can connect to both WEP and WPA connection without changing or deleting anything.
After installation the Network Manager found all available connections, I put in the SSID and Password and away I went surfing the web.

Was up and running with internet, email and chat straight out of the box. I love Gaim, still to export my contacts to Evolution and always used Firefox in WinXP. 

I've sorted out after reading the easy to use Ubuntu Guides how to mount drives, setup Sipgate using Ekiga, DVD playback, DVD burning, DVD ripping, playing mp3's and adding/deleting music in my iPOD Mini. 

All I need to sort out is syncing to my Nokia N73 and I may consider reformating the windows partition with WinXp on it.

Ubuntu Rocks.:guitar:
Ah, I haven't tried to use WPA on Feisty yet (only need it when I go to my dad's place), but when I set it up I was using Dapper and the howto said to # out everything but lo, and lo and behold, it worked.  I upgraded to Edgy and kept that config, and it worked.  Someone in the Feisty part of the board said that after doing that their WPA started working too though.  

Have you tried that "PalmOS Devices" thing in System > Preferences?  Or if it has bluetooth, you might be able to use gnome-bluetooth (have to apt-get it)

---

