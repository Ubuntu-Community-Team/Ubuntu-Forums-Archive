---
title: "[SOLVED] Screensaver isn't functional"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-10
I'm running Xubuntu 7.10 on a Compaq Presario 5WV254 5000 Series with an 800Mhz AMD Duron Processor & 313mb of ram. Ubuntu has been great so far and I'm loving the experience but for reasons unknown my screensaver hasn't been functional since day one of installation. No matter which screensaver I specify, all I get is a black screen and, although I've checked the option for it to lock my screen, it won't even lock. It **is** turned on and I've tried several different screensavers to no avail. Also when I try to disable the screensaver because its getting on my nerves, it still goes to the screensaver after 30 minutes of inactivity. Even if I set it to activate after two hours of inactivity it still comes on after 30 mins. I Would someone please help me trouble-shoot this problem? Thanks.

---

### Post by nikoPSK on 2008-01-10
You haven't specified the screensaver I am guessing? Goto System->Preferences-> Screensaver then choose. Does it work in preview for you? Also, some require graphics card drivers. Do you have them?

---

### Post by Semong on 2008-01-11
bump

---

### Post by nikoPSK on 2008-01-11
bump bump bump! Look up at my post, does that work? :)

Best,
nikoPSK

---

### Post by zabien1970 on 2008-01-11
It may not be your screensaver but your monitor going to sleep.
System>Preferences>Power Management
There is a setting to put the monitor to sleep after x minutes.

---

### Post by Semong on 2008-01-12
No niko I thought I made it clear in my post that I did specify a screensaver. In fact I specified several of them and none worked. Thanx for the quick reply anyhow :). I would imagine that zabien is hitting more near to the mark however there is no Power Management in my Settings Manager. I've opened everything in my settings and power management is no where to be found.

---

### Post by nikoPSK on 2008-01-12
> **Semong said:**
> No niko I thought I made it clear in my post that I did specify a screensaver. In fact I specified several of them and none worked. Thanx for the quick reply anyhow :). I would imagine that zabien is hitting more near to the mark however there is no Power Management in my Settings Manager. I've opened everything in my settings and power management is no where to be found.

no, no. Try running that command, it will reconfigure xorg and possibly fix the issue. :)

---

### Post by Semong on 2008-01-12
> **nikoPSK said:**
> You haven't specified the screensaver I am guessing? Goto System->Preferences-> Screensaver then choose. Does it work in preview for you? Also, some require graphics card drivers. Do you have them?


umm I dont see any command... lol possibly lack of sleep and irritation but I see no command. Oh and by the way, I do have a graphics card, it is detected and the screensavers do work when I test them.

---

### Post by nikoPSK on 2008-01-12
I thought I posted it... here:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by Semong on 2008-01-12
Niko your the man. Finally the screensaver is working and it locks the screen and I'd give you 50 thanks if I could. Would you mind telling me how to mark this thread as solved though, because I dont see an option for it and putting [SOLVED] in the title doesnt seem to work so well.

---

### Post by nikoPSK on 2008-01-12
You can do so like this:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK
PS: glad I could help you, enjoy linux.

---

### Post by The Pinny Parlour on 2008-01-12
Great stuff.   I followed your instruction and it hasn't changed a thing, I still can't get my screensaver working.   What's the advice now?

Thanks

---

### Post by nikoPSK on 2008-01-13
> **The Pinny Parlour said:**
> Great stuff.   I followed your instruction and it hasn't changed a thing, I still can't get my screensaver working.   What's the advice now?

Thanks

It would help to notify who's instructions :). Did you try reconfiguring xorg?

---

### Post by The Pinny Parlour on 2008-01-13
> **nikoPSK said:**
> It would help to notify who's instructions :). Did you try reconfiguring xorg?

Cheers mate, I worked it out.  Computers....ah they sh*t me sometimes.

---

### Post by xunil76 on 2008-01-13
you may want to post up what you did to solve the problem, to save others some time later on....and maybe even yourself at a later date, if you forget how to do it.....

---

### Post by nikoPSK on 2008-01-13
> **xunil76 said:**
> you may want to post up what you did to solve the problem, to save others some time later on....and maybe even yourself at a later date, if you forget how to do it.....

well, I helped him solved his problem with this command, might help you.

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

nikoPSK

---

### Post by Semong on 2008-01-18
> you may want to post up what you did to solve the problem, to save others some time later on....and maybe even yourself at a later date, if you forget how to do it.....

Yeah seriously because reconfiguring xorg worked for a day or so then my screensaver stopped working again. I then tried reconfiguring xorg again and it never worked after that. Finally I got fed up with all the bugs and problems I'd been having with Xubuntu so I switched over to Ubuntu 7.10. Everythings working as it should now and I can finally say I'm 100% satisfied with linux.

---

### Post by asg74 on 2008-01-23
Finally ..... I got the screensaver in 7.10 to work (only took 4 months). Easy fix for all 

add this to  xorg.conf which is located in /etc/x11

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

Enjoy your screensaver 

Adam 
State Line Pizza - Dyer, IN

---

