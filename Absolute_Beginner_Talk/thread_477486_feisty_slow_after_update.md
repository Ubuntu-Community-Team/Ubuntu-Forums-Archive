---
title: "feisty slow after update"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-06-18
I finally installed feisty on computer, and everything was working great. Then ubuntu asked if I wanted to download and install 66 upgrades and I did, now everything is slow. It takes about a minute to open any applications, and even starting up the desktop takes awhile. Is there anything I can do, or should I reinstall feisty?

---

### Post by Jimmyfj on 2007-06-18
Hi

Need more info on your system, specs about your computer

---

### Post by orwellus on 2007-06-18
I have 256 of RAM and 12 GB on harddrive. I'm not sure about some of the rest. But once, again, feisty was working fine on my system, desktop and applications loaded quickly, and without any hassel. It only started going slow after I downloaded and installed ubuntu's 66 upgrades.

---

### Post by codypumper on 2007-06-18
Do you have a video/graphics card? If so, what is it?

---

### Post by orwellus on 2007-06-18
I do have a video/graphics card. I'm not sure what kind though. But I can play dvds without any problems. And the flash player works when I go to YouTube. Also, other versions of Ubuntu including 6.10 and Kubuntu also work okay on my computer. So I'm not sure what's going on. Feisty worked too, it was just something about those upgrades that messed something up.

---

### Post by codypumper on 2007-06-18
Yes, I understand. Feisty messed with my graphics card driver, which I'm waiting for an update for.
Regardless, what type of computer do you have (brand)? Laptop or Desktop?

---

### Post by orwellus on 2007-06-18
I have an IBM thinkpad A21e (I think that's the model). It's a laptop, and I've heard that ubuntu sometimes has problems with laptops, but I never had any problems when I used edgy. I did a clean install of feisty from the cd that ubuntu sent me.

---

### Post by codypumper on 2007-06-18
Haha, same here, almost. I have Thinkpad t23.
Could you go to System->Preferences->Hardware Information.
When the window pops up, could you check for "Savage" anywhere in the list, and tell me if its there?

---

### Post by orwellus on 2007-06-18
Oh shoot. I guess we'll have to let this question stew a bit until I get home from work and can check my computer. Is that "SAVAGE" what's messing everything up?

---

### Post by codypumper on 2007-06-18
With the Feisty updates, there was a bug for most "Savage" type graphics cards. This causes various problems for people from speed, to not being able to use wine. Regardless, you could try diving into a graphic card driver recompiling (I tried but didn't get anywhere), or wait for Ubuntu to update and submit a bug report about the problem. 

That is, if you do have a Savage graphics card.

---

### Post by orwellus on 2007-06-18
Okay. I checked, but couldn't find anything marked "SAVAGE". I think my graphic card might by "RAGE" though though I'm not entirely sure. I liked Feisty when it worked, especially the KDE like icons in OpenOffice, but I guess I'll head back to Edgy until the Kubuntu 7.0.4 I order gets here.  Thanks for trying. In the end If it works, it works, if it doesn't, it doesn't.

---

### Post by codypumper on 2007-06-18
Ah, okay. Searched around, and I'm not sure that your problem is related to your graphics card. It may still be. 
Regardless, since you said it slowed after the update, you may want to just wait for another update to fix. Unless of course its killer slow. Then, you may want to look around for issues with *Ati Rage Graphics Cards*, primarily on Thinkpads. Of course, there is the slight chance its not video card related though...

Sorry, but I don't know.

---

### Post by atte on 2007-06-20
maybe a long-shot but for me it helped to install syslog-ng (replaces syslog).

---

### Post by kakk on 2007-06-21
Well, I see something similar on my machine. Any action can freeze machine for 30sec or so, and it does so quite often. I have a clean install of 7.04 on a pentium-M 1.7GHz with 60G of hdd and 1GRAM. Graphics is intel 915. Otherwise it is very nice and fast.

---

### Post by bootslap on 2007-06-21
Same problem with me ... Seems to be a pretty common problem...

---

### Post by kakk on 2007-06-21
> **kakk said:**
> Well, I see something similar on my machine. Any action can freeze machine for 30sec or so, and it does so quite often. I have a clean install of 7.04 on a pentium-M 1.7GHz with 60G of hdd and 1GRAM. Graphics is intel 915. Otherwise it is very nice and fast.

Actually I just tried fedora 7 and it is the same. Now I have kubuntu 6.10 and everything is just fine.

---

### Post by kakk on 2007-06-21
Actually it seems to be known bug

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)

and the problem seems to be the cd drive, Try to put something on the drive (cd or dvd I mean) and it should work. Hopefully solved soon.

---

### Post by kakk on 2007-06-22
Ok, I upgraded from 6.10 to 7.04 and I can use the system with the old kernel 2.6.17-11-generic. So if you did not delete the old kernel during the update, your system should be usable.

---

