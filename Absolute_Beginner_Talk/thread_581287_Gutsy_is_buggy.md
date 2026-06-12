---
title: "Gutsy is buggy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-10-19
I upgraded my feisty to gutsy and it acts really buggy. I always watch my system monitor when the computer is running and it was very smooth in feisty, but now looks like an encephalogram of a psychiatric patient. Visual effects is also buggy and causes some delays and instabilities.

Also, I miss one thing in feisty, which I can't reproduce in gutsy: When the notebook was open, it always remained active, that means was never considered "idle". And When I would close the lid and then open again, it was locked. I would enter the password and it would be unlocked. These were very useful when working with torrent downloads, because I often leave computer overnight.

Now, in gutsy, I can't reproduce this "locking" effect when I close the laptop lid. It should show blank screen, what it does, but then it has problems of "regaining consciousness" and mostly I have to restart computer to be able to work again. Any ideas?

---

### Post by skymera on 2007-10-19
hmm ive always been told upgrades are buggy.
id do a fresh install tbh.

also i like your metaphor :D [quote=o-Pos] encephalogram of a psychiatric patient [/quote]

---

### Post by Tony3286 on 2007-10-19
When you do a fresh install,if I have already backed up my /home directory from Feisty, can I just copy that into Gutsy to get all my preferences back? Is there a special way of doing that? I was planning to wait about a month before  attempting to install Gutsy so they could get all the bugs out..

Tony

---

### Post by O-pos on 2007-10-19
I spent so much cumulativetime in setting and personalizing things in ubuntu that I think I won's be able to do these things again if I fresh-install gutsy..

---

### Post by twiceasworn on 2007-10-19
Yeah,  I pretty much never upgrade until a couple months after the release, although since Feisty is LTS, I will probably stay with it for quite a while.  Very stable and it just works.

---

### Post by tsg1zzn on 2007-10-19
Disable indexing, kill trackerd and see if it makes any difference.

---

### Post by Austin_KW on 2007-10-19
You should be able to restore your home folder. I would use tar to save some space on the archive, but I guess you could just use "cp -a" 

But this time put /home on its own partitions so you will never have this problem again.

---

### Post by LowSky on 2007-10-19
> **twiceasworn said:**
> Yeah,  I pretty much never upgrade until a couple months after the release, although since Feisty is LTS, I will probably stay with it for quite a while.  Very stable and it just works.

 Dapper (6.06) is the LTS not fiesty

---

### Post by victorche on 2007-10-19
> **twiceasworn said:**
> Yeah,  I pretty much never upgrade until a couple months after the release, although since Feisty is LTS, I will probably stay with it for quite a while.  Very stable and it just works.

Feisty is ***NOT*** LTS ;)

The first LTS version was Dapper, the next one will also be LTS (8.04 - Hardy)
We have LTS after every 3 releases:

4.10 - Warty (Normal)
5.04 - Hoary (Normal)
5.10 - Breezy (Normal)
**6.06 - Dapper** (**LTS** - it was supposed to be 6.04, but it was delayed for 2 months)
6.10 - Edgy (Normal)
7.04 - Feisty (Normal)
7.10 - Gutsy (Normal)
**8.04 - Hardy** (**LTS**)

;)

---

### Post by atlfalcons866 on 2007-10-19
the next release Hardy Heron is LTS

---

### Post by O-pos on 2007-10-19
Well, it's indeed buggy, but I still don't regret that I upgraded my OS because it has some very nice features and hope that most of the principal bugs will be fixed in next month or two.

---

### Post by rofthorax on 2007-10-19
So releases are numbered year and month, that's cool.. 

The next release the LTS is slated for April of next year, okay cool..

---

### Post by rofthorax on 2007-10-19
Gutsy is bugggy as hell on my Toshiba laptop, I was the guy who posted the "Toshiba Sucks" on youtube some time back (they didn't provide XP drivers, partially the reason I wswitched to ubuntu, someone said Microsoft forced them to vacate XP).. 

Anyhow, 7.10, has got some weird issues.. Sometimes it says my X server won't load, other times it can't find the repositories, but that may be my crappy internet connection from comcast, its had lots of hiccups a lot lately..   But the sound works, it didn't work at first, but it did work the second time. Was able to get wine-doors and install Firefox, as I've had bad experiences with flash in ubuntu, and loaded flash in firefox in wine, and went to my site, chann3lz, and played videos and music came through loud and clear. 

Haven't tried getting DVD/Miro to work.. Miro wont download, the Multiverse repository stalls when I try to update. I'm thinking about waiting a couple of months as someone said before doing a Gutsy update on my desktop.. The laptop is my experimental machine anyhow, its a backup laptop for my main work laptop, so I can afford to screw with it. 

 BTw, downgraded from Vista basic to XP Pro on it, and have Ubuntu.. A lot of windows zealots had a major problem with this, most said I just needed to upgrade the ram.. Most just said I was a 'tard.. And when I asked, what was the purpose for Vista? Nobody could give me a real answer..  Toshiba put the laptops on the market with inadequate RAM.. Its been making the vendors to look just as stupid as Microsoft.. I hope it tarnishes their experience such that they see the light..

---

### Post by bloodniece on 2007-10-19
I had problems with the upgrade. *All were fixed by doing a clean install. I threw all the contents of my Home on a flash drive and started over.

---

### Post by Splat! on 2007-10-19
Boy, oh, boy.

Work your buns off and never goof and who cares?

But make one mistake - - - - - -   :evil:

Splat!

---

### Post by BOZG on 2007-10-19
With regards to update problems that a lot of people seem to be talking about, are they generally Feisty to Gutsy updates or Gutsy RC to Gutsy updates?

---

### Post by O-pos on 2007-10-19
> **rofthorax said:**
> Gutsy is bugggy as hell on my Toshiba laptop, I was the guy who posted the "Toshiba Sucks" on youtube some time back (they didn't provide XP drivers, partially the reason I wswitched to ubuntu, someone said Microsoft forced them to vacate XP).. 

Anyhow, 7.10, has got some weird issues.. Sometimes it says my X server won't load, other times it can't find the repositories, but that may be my crappy internet connection from comcast, its had lots of hiccups a lot lately..   But the sound works, it didn't work at first, but it did work the second time. Was able to get wine-doors and install Firefox, as I've had bad experiences with flash in ubuntu, and loaded flash in firefox in wine, and went to my site, chann3lz, and played videos and music came through loud and clear. 

Haven't tried getting DVD/Miro to work.. Miro wont download, the Multiverse repository stalls when I try to update. I'm thinking about waiting a couple of months as someone said before doing a Gutsy update on my desktop.. The laptop is my experimental machine anyhow, its a backup laptop for my main work laptop, so I can afford to screw with it. 

 BTw, downgraded from Vista basic to XP Pro on it, and have Ubuntu.. A lot of windows zealots had a major problem with this, most said I just needed to upgrade the ram.. Most just said I was a 'tard.. And when I asked, what was the purpose for Vista? Nobody could give me a real answer..  Toshiba put the laptops on the market with inadequate RAM.. Its been making the vendors to look just as stupid as Microsoft.. I hope it tarnishes their experience such that they see the light..

I have Toshiba too. But I think that It's not up to Toshiba, but rather upgrade vs. clean install.

---

### Post by Rich78 on 2007-10-19
Is LTS classed as more stable than other releases?

I understand it's "Long term support" but is it the most stable release?  I mean if you were to use Ubuntu for a business would you choose 6.06 or higher?

Thanks

---

### Post by stchman on 2007-10-19
> **twiceasworn said:**
> Yeah,  I pretty much never upgrade until a couple months after the release, although since Feisty is LTS, I will probably stay with it for quite a while.  Very stable and it just works.

Feisty is not LTS, Dapper 6.06 and the next release Hardy Heron (8.06) will be LTS as well.

---

### Post by Wiebelhaus on 2007-10-19
> **skymera said:**
> hmm ive always been told upgrades are buggy.
id do a fresh install tbh.

also i like your metaphor :D

I'm digging that as well.

---

### Post by Billy_McBong on 2007-10-19
> **BOZG said:**
> With regards to update problems that a lot of people seem to be talking about, are they generally Feisty to Gutsy updates or Gutsy RC to Gutsy updates?
[COLOR="Blue"]i think most the problems are with people upgrading from Feisty
there isn't much differenance between the RC and final release so there shouldn't be lots of problems with upgrading from that[/COLOR]

---

