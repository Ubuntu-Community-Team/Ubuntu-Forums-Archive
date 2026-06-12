---
title: "Upgrade from Hardy Heron Alpha to its Final Release"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-11-27
I am thinking of doing the following:

Installing Hardy Heron Alpha later in November, when it is released. (It will be my 1st installation of Ubuntu.)

Then doing an upgrade to the Final Release in April, when it comes out.

Should this be a simple matter?

---

### Post by PmDematagoda on 2007-11-27
It is simple enough, but do you really want to use a developmental version of Ubuntu as your first Ubuntu OS which would most likely have a lot of bugs especially considering that it is an Alpha release. It would most likely make you hate the OS due to it being buggy even though this is because it is normal for an OS that is in development. 

Why don't you just use Ubuntu 7.10 or Ubuntu 6.06 which are less buggy and therefore easier to use?

---

### Post by dptxp on 2007-11-27
Depends on how many system crashes you get.

---

### Post by CosmicFlux on 2007-11-27
Yeah, it's much better to use a stable release as your main working OS rather than have to encounter problems in an Alpha version. If you had another computer you could load it onto that and test it out, or you could dual boot.

---

### Post by yeehi on 2007-11-27
How buggy was the last alpha release of a LTS Ubuntu? 
Would I be able to upgrade directly to the forthcoming fiinal release of Hardy Heron if I install Gutsy Gibbon now?

---

### Post by PmDematagoda on 2007-11-27
You cannot compare how buggy Ubuntu 8.04 would be by simply comparing it to Ubuntu 6.06 as different releases have different features and packages and therefore will have a different number of bugs and different types of bugs.

You can upgrade Ubuntu 7.10 to Ubuntu 8.04 using the Update Manager in Ubuntu or Adept in Kubuntu. In any case why are you worrying about Ubuntu 8.04 when it still has many months of development and testing before it's official release on April 2008 which is half an year away.

---

### Post by tszanon on 2007-11-27
I've never used an under-development version, but I've read here in the forums that:
1. updates are frequent. Almost everyday there are new updates;
2. updates can break the installation.

So, if you're not an advanced user, it's not recommended that you use such version. It would be better if you used Dapper, Feisty or Gutsy (6.06, 7.04 or 7.10) instead.

---

### Post by viking777 on 2007-11-27
> **yeehi said:**
> How buggy was the last alpha release of a LTS Ubuntu? 
Would I be able to upgrade directly to the forthcoming fiinal release of Hardy Heron if I install Gutsy Gibbon now?

They are always buggy that is why they are Alpha. I am running it now (but I dual boot with Gutsy), it has several bugs, no bad ones but bugs just the same. I seriously suggest that you dual boot if you want to test Hardy.

The process of updating is simple you just install Gutsy then go to /etc/sources.list and everywhere is says 'gutsy' you change it to 'hardy'.

You then do apt-get update, apt-get upgrade and apt-get dist-upgrade you will then have the present version of Hardy. Then as long as you keep installing all the updates you will have the final version of Hardy by the time it is released, no need to download it again unless you want to.

---

### Post by roaldz on 2007-11-27
Please do us and especially yourself a favor, and pick 6.06 or 7.10, hardy is a no-go right now. Gutsy (7.10) is stable enough for normal desktop use, 6.06 is just stable.

---

### Post by The Cog on 2007-11-27
Just the fact that you ask the question suggests that you are not ready for the trials of an alpha relese, which is pretty-much guaranteed to crash or at least dump you in a B&W text screen from time to time. I think you should play safe and go for Gutsy for now.

---

### Post by kdarkentity on 2007-12-17
Whats strange is i've been using Hardy Heron for about an hour or so now and surprisingly enough it seems to be fairly stable, In some aspects it might even be more stable than 7.10  , still i would recommend to use 7.10 for the time being. I actually am still using 7.10 primarily , i have 8.04 installed on a separate 7 gig partition.

---

### Post by macogw on 2007-12-17
> **kdarkentity said:**
> Whats strange is i've been using Hardy Heron for about an hour or so now and surprisingly enough it seems to be fairly stable, In some aspects it might even be more stable than 7.10  , still i would recommend to use 7.10 for the time being. I actually am still using 7.10 primarily , i have 8.04 installed on a separate 7 gig partition.

It might be stable now, but when you get an update it might break.  You won't know how to fix it.  Others may know how to fix it, but you might be stuck in a world of command line.  You should do at least a few months on a stable release to get your feet wet and learn everything you can about how it works.  Then try a beta, so you see how minor instability works.  The next release after that, you can try an alpha.  I used Ubuntu for 6 months before trying an alpha, and I made sure I was 100% comfortable in the terminal and knew my way around the filesystem fairly well first.

Just because it will be LTS doesn't mean the first alpha will be anywhere near stable.  It'll basically be Gutsy with lots of new packages that don't necessarily work together flying through your updates constantly.

---

### Post by louieb on 2007-12-17
> **yeehi said:**
> How buggy was the last alpha release of a LTS Ubuntu? 
Updates for Dapper for killed quite a few installations: The great xorg update was one that had the forum buzzing.  I know it trash my GUI. Also remember one  Kernel  update for Dapper that killed wifi on a number of PCs and those were after the release. 
Alpha releases  are for throwing upgraded, updated, or new software and see what happens.   The good new is if you survive it you probably be pretty good at backing up and restoring your data.

---

### Post by macogw on 2007-12-17
> **louieb said:**
> Updates for Dapper for killed quite a few installations: The great xorg update was one that had the forum buzzing.  I know it trash my GUI. Also remember one  Kernel  update for Dapper that killed wifi on a number of PCs and those were after the release. 
Alpha releases  are for throwing upgraded, updated, or new software and see what happens.   The good new is if you survive it you probably be pretty good at backing up and restoring your data.

Hey they killed wired internet on a lot of laptops after Dapper's release (in September, I think..that was when I learned why there are old kernels in the list), just a couple weeks after a bunch of people's video got whacked.

---

### Post by nowshining on 2007-12-17
as said by others buggsy yes, however upgrading is a huger risk then downloading and installing via a new install. Also as long as u keep updated for Hardy there is NO need to re-install unless u want a clean install -- if not, and u clean installed, then u'll already just  before the release date have the whole version of hardy heron so there would be actually really no need to re-install again as again u kept up with all the updates.

---

### Post by macogw on 2007-12-17
Though I'd do that reinstall from the release candidate to avoid release-day's slow servers.

---

### Post by bodhi.zazen on 2007-12-17
FYI : I am running Hardy now, but that is me and I do not advise it to users wanting a stable, bug free os.

Well, no OS is bug free, but some have less bugs then others.

At any rate, in my experience, when you run start with an Alpha there will be bugs. When the Beta is release, upgrading may or may not fix the bugs in your alpha, you may need to fix them yourself (if you can) or re-install the Beta. When you upgrade from Alpha -> beta things may break.

ditto for all releases up to the final release.

So, I would not discourage you from running Alpha, however I would say expect bugs and you are on your own to fix them.

I would NOT expect to be able to upgrade, without bugs, to the beta or RC or final release as I have never been able to do this with previous Alphas. I could likely fix a good chunk of problems, but why bother ? I install Alpha, upgrade to check it out, and if there are bugs, re-install the latest version.

Alpha is for testing, so report bugs back to the developers so they can try to address them as best they can.

---

