---
title: "why is ubuntu is slower than xp on my computer?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-12-05
im pretty new to linux but really liking it. ive almost completely converted from xp and only use xp if i need to now. but i have noticed windows xp is considerable faster. expecially while browsing the internet. when im using firefox in xp pages come up in a flash and ubuntu is more than little sluggish in comparison.

also i posted a while back but didnt really get an answer. whenever i update, install or unistall sofware i get this error now

E: cupsys: subprocess post-installation script returned error exit status 1
E: ntp: subprocess post-installation script returned error exit status 1

i cant figure out what i did to cause this to happen. i thought it might be automatix because i installed it on both my desktop and laptop and now there both doing it. but then i tried to install moblock on one of my servers the other day and it gave the same thing i think. but moblock wouldnt install for some reason. where as most programs seem to install regardless of the error.

oh and last thing. can anybody help with a visiontek x1650 pro video card? i know there isnt much support for ati...

thanks guys.

---

### Post by JillSwift on 2007-12-05
FireFox was a bit sluggish for me because it was trying IPv6 first, timing out, then trying IPv4.

You can turn off the IPv6 but putting "about:config" in the URL bar, and in the filter line of the config page put "IPv6". You should see a line "network.dns.disableIPv6", set this to "True". You should see a bit of a boost in speed when loading pages.

---

### Post by jflaker on 2007-12-05
Another note for Sticky......Instant speed boost!

---

### Post by uknowho008 on 2007-12-05
cool! that deffinetly made a difference. still not quite as fast as xp i dont think. but good none the less. im sure the settings are the same in the xp version of firefox right? so im guessing thats not the only problem.

---

### Post by SOULRiDER on 2007-12-05
> **uknowho008 said:**
> cool! that deffinetly made a difference. still not quite as fast as xp i dont think. but good none the less. im sure the settings are the same in the xp version of firefox right? so im guessing thats not the only problem.

Thats probably more psicological than anything else, they are most likely going at the same speed.

---

### Post by uknowho008 on 2007-12-05
i dont think so. i was denying that xp was better in anyway for a long time. but everytime i go back to xp its just faster.

---

### Post by MikeyXX on 2007-12-05
> **uknowho008 said:**
> i dont think so. i was denying that xp was better in anyway for a long time. but everytime i go back to xp its just faster.

I find my xp booted in under a minute. My Ubuntu takes 3-4 minutes to boot. Otherwise I don't notice a speed difference.

---

### Post by Papa-san on 2007-12-05
I did this, and agree... My firefox is a bit faster now!
Thanks!

(I never knew that these controls were there... LOL) Now I'm looking at further tweaking!
I have timed my boot-up on both, and the XP is about 17 seconds quicker on my box. It's definitely 17 seconds I'm willing to spend because I know how much I prefer Ubuntu.

---

### Post by JillSwift on 2007-12-05
You can [COLOR=RoyalBlue]_[speed up Ubuntu boot times]("http://ubuntuforums.org/showthread.php?t=89491")_[/COLOR].

---

