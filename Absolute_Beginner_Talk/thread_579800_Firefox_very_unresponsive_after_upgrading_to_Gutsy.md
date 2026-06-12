---
title: "Firefox very unresponsive after upgrading to Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-18
just finding that firefox is now often freezing and crashing after upgrading to gutsy, anyone else experiencing this?

---

### Post by stchman on 2007-10-18
> **dynamethod said:**
> just finding that firefox is now often freezing and crashing after upgrading to gutsy, anyone else experiencing this?

I recommend a fresh install and not an upgrade.

---

### Post by dynamethod on 2007-10-18
unfortunatly for me a fresh install is not an option for me :S

---

### Post by stchman on 2007-10-18
> **dynamethod said:**
> unfortunatly for me a fresh install is not an option for me :S

Why would that be?  You can download the .iso and make an install CD.

---

### Post by dynamethod on 2007-10-18
ive got no dvd/cd burner(the device), and i have about 500mb's left to use on my HD, on top of that, ive got alot of uni stuff that i dont want to loose from reinstalling,

---

### Post by p_quarles on 2007-10-18
One thing you can try:
1) In the address box, type about:config and press enter
2) In the box labeled "filter", enter "network.dns.disableIPv6"
3) Click on this setting, and change the value to "true." 

That's one of the most common problems. Let us know if that works.

---

### Post by philinux on 2007-10-18
Mines running about the same.

Off topic - I'd get a burner or an ext hard drive i just got errors from a HD and if you got important stuff it needs backing up pronto.

---

### Post by dynamethod on 2007-10-18
> **p_quarles said:**
> One thing you can try:
1) In the address box, type about:config and press enter
2) In the box labeled "filter", enter "network.dns.disableIPv6"
3) Click on this setting, and change the value to "true." 

That's one of the most common problems. Let us know if that works.

seems to be working better now, thanks! :)

---

### Post by stchman on 2007-10-18
> **dynamethod said:**
> ive got no dvd/cd burner(the device), and i have about 500mb's left to use on my HD, on top of that, ive got alot of uni stuff that i dont want to loose from reinstalling,

CD/DVD burners can be had at Newegg for under $30.  As far as the hdd space, I don't know how old your system is but you could probably delete a bunch of old junk that is just taking up space.

How did you install Ubuntu on your system to begin with?

If you want, PM me and PayPal me like $2 (shipping) and I will send you Gutsy on CD.  There is always the free CDs from Ubuntu but they can take months to arrive.

---

### Post by dynamethod on 2007-10-18
i orignally got feisty from shippit, and installed with the live CD, as for the hardware upgrades, im a very poor student, and finding a part time job round here is not easy :S

---

### Post by stchman on 2007-10-18
> **dynamethod said:**
> i orignally got feisty from shippit, and installed with the live CD, as for the hardware upgrades, im a very poor student, and finding a part time job round here is not easy :S

Do you have any friends that could burn you a CD of Gutsy?

---

### Post by dynamethod on 2007-10-18
yeah do actually, but even so, would i be able to upgrade this gutsy with the live CD version? i cant format or i loose too much work :S

---

### Post by p_quarles on 2007-10-18
No, you couldn't upgrade with the CD. If you've got the dist-upgrade working okay, you're fine. No need to do anything else.

---

### Post by steve.horsley on 2007-10-18
You really should have some kind of backup you know. Kicking yourself for not doing backups goes on for a long time after an unexpected failure - I still kick myself occasionally 5 years later, when I miss stuff I can't replace.

---

### Post by dynamethod on 2007-10-18
i know, ive learned an important lesson here :S

---

### Post by mivo on 2007-10-18
Well, actually, the real issue is that you don't have a separate /home partition. :) If you had one (say, 10 GB for /, a bit for swap and the rest for /home), you could safely re-install Gutsy from scratch without losing any of your personal files or settings. When/if you set up a new system, this may be worth considering. :)

---

### Post by p_quarles on 2007-10-18
> **mivo said:**
> Well, actually, the real issue is that you don't have a separate /home partition. :) If you had one (say, 10 GB for /, a bit for swap and the rest for /home), you could safely re-install Gutsy from scratch without losing any of your personal files or settings. When/if you set up a new system, this may be worth considering. :)
That would  make it easier to upgrade, but that's absolutely not a substitute for keeping backups of important data. Hard drive failure doesn't spare the home partition. 

In any case, the OP's question was about getting the dist-upgrade to work. It's not always smooth, but it can be done with some tweaking. Insisting that he needs to reinstall from a new disk is kinda off-topic IMO.

---

### Post by mivo on 2007-10-18
No argument there, I'm in perfect agreement with the need to backup data. :) It can be nicely automated, too -- I use an external disk for scheduled backups and an USB stick for spontaneous backups (documents and such), A separate /home partition just helps greatly with upgrading/reinstalling the core system (though that would only be of limited help here since he doesn't have a burner).

---

### Post by orthopod on 2007-10-20
Solved my problem - thanks

---

### Post by frank002 on 2007-10-20
> **p_quarles said:**
> One thing you can try:
1) In the address box, type about:config and press enter
2) In the box labeled "filter", enter "network.dns.disableIPv6"
3) Click on this setting, and change the value to "true." 

That's one of the most common problems. Let us know if that works.
I followed your advice and disabled IPv6 and that sped up Firefox. It did not resolve the issue with Evolution and Thunderbird. These two programs are still very slow. Feisty was much better. There was no need to disable IPv6 with it. Maybe they rushed to get 7.10 out. 
 Anyway, thanks for your advice.

---

### Post by Buddy Gurt on 2007-11-02
> One thing you can try:
1) In the address box, type about:config and press enter
2) In the box labeled "filter", enter "network.dns.disableIPv6"
3) Click on this setting, and change the value to "true."

That's one of the most common problems. Let us know if that works.
Unfortunately, this didn't work for me. After my upgrade to Gutsy, everything worked fine, but Firefox suddenly takes a lot of time loading webpages and sometimes even stops responding (happens with every page!). No problems with download speed, e.g. epiphany still works perfect, and doesn't have the "Firefox problem". Must be something in Firefox, but I can't figure out what.

---

### Post by Partyboi2 on 2007-11-02
You could try:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
It helped to get my pages loading up faster

---

