---
title: "Starting Ubuntu..."
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by octomber on 2007-03-07
Hi !
A few days ago I installed ubuntu 6.10 in a partition of my hard disc and now I make the first steps with it !
Could somebody please answer  me the following questions ?
- How can I edit my TFT screen's resolution ? The best option I have via the screen resolution button of the system menu is only 800 to 600, which is very uncomfortable (the windows do not fit to the screen etc )
- Do I need a firewall, an antivirus and an antispyware software ? I saw somewhere in the forum that ubuntu actually does not need a firewall. Is that so ? I tried to find firestarter in my synaptic package manager but I couldn't.
- I have a HP handheld that runs Windows Mobile 5.0. Can I install Active Sync in Ubuntu an work with it ?
- Where do I find desktop backgrounds and screensavers ? I can't stand my new, promising Ubuntu software looking worse than Windows XP !

Thanks !

---

### Post by milton1 on 2007-03-07
resolution problems could be an issue with video drivers. search for install tips for your card of choice (ati, nvidia, etc).

antivirus: not necessary, but if you want one, try clamAV.

firewall: firestarter is a nice toy. If you are not finding it, you may need to enable the universe and multiverse repos by removing the # characters in front of them in /etc/apt/sources.list 

handheld connection may have to be done using utilities built into gnome/kde. They should be there, and they should work. you may have to install them with synaptic.

---

