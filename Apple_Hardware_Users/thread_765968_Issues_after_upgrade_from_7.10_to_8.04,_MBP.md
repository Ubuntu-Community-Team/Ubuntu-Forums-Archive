---
title: "Issues after upgrade from 7.10 to 8.04, MBP"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by hellmitre on 2008-04-24
Heya, kids and gurus of the Hardy Heron Ubuntu distro. I have been running Ubuntu 7.10 on my 2.4 Ghz 15 inch MBP, dual-booted with Mac OS X Leopard, for about six months now, and prefer Linux to Leopard. I just upgraded from 7.10 to 8.04, and have a few bugs I'd really like to work out.
First off, my optical drive isn't working at the moment, which means a clean install is impossible unless I find some other way to install it.

Issue one, and most important: wireless doesn't work. I had it working with the madwifi drivers very nicely; a bit buggy but totally manageable and functional. After the update, wireless won't function at all -- not even recognized by Linux. I need wireless to work because I am rather nomadic and couch-hop between friends' houses on the weekends. 

Issue two, less-but-still-important: no sound. Volume controls appear fine, and the audio drivers appear to be correctly installed. 

Any help anyone could give on either of the issues (someone ride to my wireless rescue, pls, kthxbai) would be greatly appreciated.

---

### Post by cyberdork33 on 2008-04-25
> **hellmitre said:**
> Issue one, and most important: wireless doesn't work. I had it working with the madwifi drivers very nicely; a bit buggy but totally manageable and functional. After the update, wireless won't function at all -- not even recognized by Linux. I need wireless to work because I am rather nomadic and couch-hop between friends' houses on the weekends.  I am pretty sure you have to redo the madwifi stuff to get it working again. I hope you have the revision that you used before since there are a lot of people having bad luck with the newer revisions.

> **hellmitre said:**
> Issue two, less-but-still-important: no sound. Volume controls appear fine, and the audio drivers appear to be correctly installed.Try some of the options listed here:
 [http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Crackling_Sound_on_the_left_Channel)

---

### Post by hellmitre on 2008-04-25
I hung around in the #ubuntu IRC channel and prodded people for answers to my wireless question, and was shot in the direction of madwifi-ng. It's some sort of patch ... heh... so I downloaded and compiled it, then installed wicd (a different and weird but functional network manager) and poof, wireless worked. My issue, AFAIK, was my computer thought its wireless connection was wifi0 - which it was in 7.10 - and Hardy had renamed the wireless card ath0. So I changed that and got it working.

As for the sound: open a terminal and type alsamixer. For each section that has a bar above it, press Up until it's at 100, then Right over to the next one. Rinse, repeat. Got my audio jack working that way, and I normally use headphones so it's all good. Speakers still no-go, though.

Final issue: Emerald is, oddly, not working, even though the Emerald Theme Manager will run. Any help?

---

### Post by cyberdork33 on 2008-04-25
> **hellmitre said:**
> I hung around in the #ubuntu IRC channel and prodded people for answers to my wireless question, and was shot in the direction of madwifi-ng. It's some sort of patch ... heh... so I downloaded and compiled it, then installed wicd (a different and weird but functional network manager) and poof, wireless worked. My issue, AFAIK, was my computer thought its wireless connection was wifi0 - which it was in 7.10 - and Hardy had renamed the wireless card ath0. So I changed that and got it working?
it should have been called ath0 in gutsy too, but whatever. Glad you got it working.

---

