---
title: "ahhhh... a black screen :'("
date: 2009-09-18
forum: Apple Hardware Users
---

### Post by gwydionwaters on 2009-09-18
and i just got everything working nicely

i upgraded from 8.10 to 9.04 and noticed that suspend was no longer an option in power management settings, so i chose hibernate instead. i tried closing the lid, on my powerbook ppc arch, it powered down like it should. now i can only boot through yaboot then that evil little cursor shows up and sits there looking at me without blinking. i can successfully boot my system using an ibex install cd in rescue mode, but have two problems thereafter. i don't know what to do to fix the problem. and i don't know how to start my desktop properly. i tried just startx but my mouse/keyboard didn't work, so i tried starting mouseemu first but it seems to hang on starting, so i ctrl-c and try again but with restart and it seems to be running and restart ok. still no mouse or keyboard after starting x though. i'd really like to not have to re install as i would have to reconfigure, upgrade, get drivers going again.. you understand :)

and sorry but i highjacked a couple other posts in my panic to find answers, thanks for reading and hopefully i can fix this

---

### Post by crocowhile on 2009-09-18
you should be able to start gnome with

sudo /etc/init.d/gdm start

---

### Post by gwydionwaters on 2009-09-18
i tried that and i get the low color/resolution window and can still not use my mouse or keyboard. startx worked better, it looked normal but i could not control anything :confused:

I did delete my xorg.conf files because I thought they may be a contributor due to my previous version not using these and using hal. That is probably why I get the color problem. I'm more concerned about getting it to boot  through yaboot again.

---

### Post by gwydionwaters on 2009-09-19
I gave up, I missed my computer. I'm starting fresh with ibex and going for an immediate upgrade. This time I made a rescue partition which I will back up files and configurations in :) I am still interested in figuring out why it wouldn't begin to boot the kernel.

---

