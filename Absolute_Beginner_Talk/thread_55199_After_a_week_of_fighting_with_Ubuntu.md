---
title: "After a week of fighting with Ubuntu"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by Willcan on 2005-08-07
I'm going back to windows.

---

### Post by az on 2005-08-07
So I looked at your other posts and they imply that you installed a mini-ram howto system and complained that it would not print.  Had you installed the full gnome desktop, you probably would not have had they troubles that you did.

---

### Post by aysiu on 2005-08-07
What was the point of this thread?

---

### Post by Knight Palatine on 2005-08-07
[QUOTE=azz]So I looked at your other posts and they imply that you installed a mini-ram howto system and complained that it would not print.  Had you installed the full gnome desktop, you probably would not have had they troubles that you did.[/QUOTE]

Well, I installed the full gnome desktop and, after a month of fighting, still can't print.

I saw a commercial utility mentioned in another post. In a last-ditch effort to get Linux to print, I downloaded the demo. It installs, but is broken. Synaptic is broken until I get this utility uninstalled, but it won't uninstall until it's installed without errors!

Multimedia apps are no treat, either.

 ](*,)

---

### Post by Willcan on 2005-08-07
[QUOTE=azz]So I looked at your other posts and they imply that you installed a mini-ram howto system and complained that it would not print.  Had you installed the full gnome desktop, you probably would not have had they troubles that you did.[/QUOTE]

Yes I did install the mini ram version.  My system (200 mhz 64Mb ram - upgrading is not an option) isn't robust enough for the full version.  The full version did work, but annoyingly slow, which is why I tried the mini-ram install.  That version wasn't all that speedy, but miles better than a full install, and well within acceptable limits.

After a week of squinting at the tiny fonts, and been unable to figure out how to get the printer working I finally gave up.

---

### Post by OttoDestruct on 2005-08-07
[QUOTE=Willcan]Yes I did install the mini ram version.  My system (200 mhz 64Mb ram - upgrading is not an option) isn't robust enough for the full version.  The full version did work, but annoyingly slow, which is why I tried the mini-ram install.  That version wasn't all that speedy, but miles better than a full install, and well within acceptable limits.

After a week of squinting at the tiny fonts, and been unable to figure out how to get the printer working I finally gave up.[/QUOTE]

I realize it sounds harsh, but you can pickup a nice computer for a pretty cheap price nowadays off eBay. I would suggest something like an iMac, as those already give you a monitor. That would be plenty enough for a full install, to run pretty smooth, and would probably allow you to print as well.

---

### Post by aysiu on 2005-08-07
[QUOTE=Willcan]The full version did work, but annoyingly slow, which is why I tried the mini-ram install.  That version wasn't all that speedy, but miles better than a full install, and well within acceptable limits.[/QUOTE] How about doing a full install and then using XFCE instead of Gnome?

---

### Post by blakamin on 2005-08-07
:-({|= 

oh well... nevermind.... and all that :-#

---

### Post by Willcan on 2005-08-08
[QUOTE=aysiu]What was the point of this thread?[/QUOTE]

Frustration

---

### Post by Willcan on 2005-08-08
[QUOTE=aysiu]How about doing a full install and then using XFCE instead of Gnome?[/QUOTE]

Okay, I can give that a shot.

Thanks.

---

### Post by aysiu on 2005-08-08
Let us know if you need any help, but I think it should just boil down to these steps:

1. In Synaptic, Reload, Search (for XFCE), mark XFCE for installation, Apply.
2. Log out.
3. Pick Session XFCE
4. Log in.

---

### Post by nocturn on 2005-08-08
[QUOTE=Willcan]Okay, I can give that a shot.

Thanks.[/QUOTE]

I second this.  It is working nicely on my old laptop (PII 333 with 128 MB RAM)

---

### Post by az on 2005-08-08
Also, not all hardware vendors are nice enough to release specs, let alone drivers for their stuff.  

That is the reality of open source.  No one is pointing a gun to your head saying that you have to run this.  It would be altogether more contructive to file abug report about the problem - maybe it can be fixed.

There is a budget for bounties and that involves issues like this, you know.

The squeeky wheel gets the grease.  But the howling hound gets shooed away.

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=azz]Also, not all hardware vendors are nice enough to release specs, let alone drivers for their stuff.  

That is the reality of open source.  No one is pointing a gun to your head saying that you have to run this.  It would be altogether more contructive to file abug report about the problem - maybe it can be fixed.

There is a budget for bounties and that involves issues like this, you know.

The squeeky wheel gets the grease.  But the howling hound gets shooed away.[/QUOTE]

Or my favorite, "It puts the lotion on its skin or else it gets the hose again"  :grin:

---

### Post by aveline on 2005-08-09
[QUOTE=OttoDestruct]Or my favorite, "It puts the lotion on its skin or else it gets the hose again"  :grin:[/QUOTE]
 If ubuntu fails to meet your needs, i highly recomend damn small linux, a knoppix derivative that is 50mb in size & has a community like this one.  On your comp I wouldn't run anything else really and it is released (a new ver) about every 4 to 6 weeks.  Not quite as user friendly perhaps but very very good and getting better with every release.

aveline

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=aveline]If ubuntu fails to meet your needs, i highly recomend damn small linux, a knoppix derivative that is 50mb in size & has a community like this one.  On your comp I wouldn't run anything else really and it is released (a new ver) about every 4 to 6 weeks.  Not quite as user friendly perhaps but very very good and getting better with every release.

aveline[/QUOTE]

No one says it....but really Ubuntu has a "recommended" system spec. I would put it at 256mb RAM, and 800+mhz processor.

---

### Post by Willcan on 2005-08-09
[QUOTE=aysiu]Let us know if you need any help, but I think it should just boil down to these steps:

1. In Synaptic, Reload, Search (for XFCE), mark XFCE for installation, Apply.
2. Log out.
3. Pick Session XFCE
4. Log in.[/QUOTE]

No joy in mudville.  I did a full install and tried the above.  Synaptic said that it had installed XFCE but it didn't show up in the session list.  So I went back in and did an apt-get install on XFCE, and installed it that way.  It still didn't show up in the session list.

Thanks for the suggestion.

---

### Post by Willcan on 2005-08-09
[QUOTE=aveline]If ubuntu fails to meet your needs, i highly recomend damn small linux, a knoppix derivative that is 50mb in size & has a community like this one.  On your comp I wouldn't run anything else really and it is released (a new ver) about every 4 to 6 weeks.  Not quite as user friendly perhaps but very very good and getting better with every release.

aveline[/QUOTE]

Thanks.  I was thinking that might be a better way to go.  That or Ubuntu-lite.

---

### Post by az on 2005-08-09
[QUOTE=poofyhairguy]No one says it....but really Ubuntu has a "recommended" system spec. I would put it at 256mb RAM, and 800+mhz processor.[/QUOTE]

Well, the only spec is more than 32 megs of memory and 1.8 gigs of hard drive space.

That is a minimum.  If you want a reccomended, well, that is subjective.  I would be fine with 128 Megs of ram and a 333MHz processor....

---

