---
title: "Moving from Ubuntu Feisty to Kubuntu 6.06"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-05-04
First off, went cold turkey from Winblows a couple of weeks ago and went straight to Ubuntu Feisty 64-bit.  It's been fun learning, but tonight I checked out the KDE desktop, and I LIKE it!  Question is, is there a way to migrate from GNOME to KDE, or am I going to have to do a fresh install?  I was also thinking at the same time to go to the LTS version (Dapper) since this is my main workhouse computer.  Any ideas?  At this very moment I'm checking out the Xubuntu so I may have to update my post.  TIA

---

### Post by Wake Rider on 2007-05-04
You don't need to go to Kubuntu. you can just install kde by itself to work beside Gnome.

I think this is the code I used (someone please correct me if I am wrong)

sudo apt-get install kde

When you come to your log in screen you go to options > sessions and select either kde or gnome. I did all of this last night, and kde and gnome are working side by side.

---

### Post by therandman on 2007-05-04
I have all three installed (GNOME, KDE, and now XFCE).  I only want to use KDE, but I originally installed Ubuntu.

---

### Post by starcraft.man on 2007-05-04
Edit: Wuups, gah, getting brain dead and not reading everything properly...

If you just want the KDE core apps and not install the 650 MB of KDE that come with Wake's command, then use this...

sudo aptitude install kde-core

I however, always prefer clean installs, thats just me.

---

### Post by bcmiller on 2007-05-04
oops... you posted while i was writing sorry for the echo

For the whole Kubuntu Install

```
sudo aptitude install kubuntu-desktop
``` 

For just KDE

```
sudo aptitude install kde-core
```


The original poster said he is going to 6.06 from 7.04.  I think you want to do this because you are using the 64 bit version and you think that 7.04 is the problem.  If this is true I suggest you install 7.04 32bit version and you should have a solid install. oh and semper fi

---

### Post by thelocust on 2007-05-04
I made the switch from Gnome to KDE and I suggest a fresh install not everything seemed to work quite right with it when I just installed KDE next to Gnome especially at startup. Since your only a week or so into it you should definitely do a fresh install especially if you want to downgrade to Dapper.

---

### Post by thelocust on 2007-05-04
If you don't want to do a fresh install [this website]("http://www.psychocats.net/ubuntu/") will tell how to do everything you want to do.

---

### Post by therandman on 2007-05-04
> **bcmiller said:**
> 


The original poster said he is going to 6.06 from 7.04.  I think you want to do this because you are using the 64 bit version and you think that 7.04 is the problem.  If this is true I suggest you install 7.04 32bit version and you should have a solid install.

Actually I want to go down to 6.06 just because I need the stability.  I had no real problems with 64-bit feisty aside from the Flash and the NVidia problems, which I have taken care of.  I will probably just do a fresh install of 64-bit Kubuntu Dapper, and then install 64-bit Kubuntu Feisty on my other PC to continue to explore and learn.

---

### Post by therandman on 2007-05-04
> **thelocust said:**
> If you don't want to do a fresh install [this website]("http://www.psychocats.net/ubuntu/") will tell how to do everything you want to do.

Thanks for the link, more interesting info to add to my files! :) Think I will try to revert to KDE-core after I finish installing.

I am having so much fun with Ubuntu, can't believe I didn't dump Windoes years ago (actually tried Red Hat about 5 or 6 years ago, and couldn't even get it installed.)

---

### Post by bcmiller on 2007-05-04
> **therandman said:**
> Actually I want to go down to 6.06 just because I need the stability.  I had no real problems with 64-bit feisty aside from the Flash and the NVidia problems, which I have taken care of.  I will probably just do a fresh install of 64-bit Kubuntu Dapper, and then install 64-bit Kubuntu Feisty on my other PC to continue to explore and learn.


Even so I would recommend that you stay away from the 64 bit version regardless of which release you are using.  I don't think that the Dapper release should be any more stable than Edgy or Feisty (except that Feisty is newer)  The LTS seemed like more of a promise to support the one version for a longer time so that someone could be assured that they didn't need to upgrade anytime soon.

I would want to take advantage of the better support for wireless and the other advances since last year.

---

### Post by teddybairs1 on 2007-05-04
Dapper may be considered more stable but you will lose more functionality if you downgrade, and it is a downgrade, from feisty to Dapper. If you haven't had any real issues with feisty, why bother? If you downgrade to dapper now, you will have to run through the entire upgrade cycle to get to the next lts version once it is realeased and that it likely to be 3 or 4 full distro upgrades. Better to stick with feisty and the update manager. If it ain't broke, don't fix it.;)

---

### Post by therandman on 2007-05-04
> **teddybairs1 said:**
> Dapper may be considered more stable but you will lose more functionality if you downgrade, and it is a downgrade, from feisty to Dapper. If you haven't had any real issues with feisty, why bother? If you downgrade to dapper now, you will have to run through the entire upgrade cycle to get to the next lts version once it is realeased and that it likely to be 3 or 4 full distro upgrades. Better to stick with feisty and the update manager. If it ain't broke, don't fix it.;)

More I think about, you're all right.  I'm gonna stay with Feisty 64-bit, and just run KDE in Ubuntu.  I'll just install 64-bit Kubuntu Feisty on my second PC.  Really want to replace Windoze on my gaming PC, but I still can't live without my games.  Anybody have a stable alternative for running Battlefield 2, Farcry, COD, etc. in Ubuntu?

I've tried to get other distros to install on my 32-bit PC's, but they don't install anywhere as easily as Ubuntu.  I got Zenwalk going on an old 1.3Ghz Celery, but since I fix things even when they're not broken :), it didn't respond well to be overwritten with Kubuntu.  Guess I will be Ubuntu4Life.

---

### Post by teddybairs1 on 2007-05-04
Yeah, I fix way to many things that aren't broken. Thus, the only reason why my Ubuntu system crashes is because I did something to it (as opposed to malware or hackers).

---

