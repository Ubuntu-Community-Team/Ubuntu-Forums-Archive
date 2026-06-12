---
title: "avant windows manager - linux newb"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by B0whunt3r on 2008-01-30
can someone tell me what is wrong here. I've followed several different tutorials and can't get this to work. the last one I tried is [http://ubuntuforums.org/showthread.php?t=351186](http://ubuntuforums.org/showthread.php?t=351186)

dan@Dan-linux:~/avant-window-navigator-0.1.1$ svn checkout [http://avant.window-navigator.googlecode.com/svn/trunk/](http://avant.window-navigator.googlecode.com/svn/trunk/) avant-window-navigator
svn: PROPFIND request failed on '/svn/trunk'
svn: Could not open the requested SVN filesystem
dan@Dan-linux:~/avant-window-navigator-0.1.1$


Also, if you have a minute can someone explain why this is all necessary to install an application? Used to windows... When these terminal screens run I don't even know what it's doing to my system.

---

### Post by Ub1476 on 2008-01-30
It's not necessary to use the terminal when installing an application. It just happen to be that most guides use the terminal instead of saying " open this, download that, click that etc.:". There's a .deb package (like .exe) on [GetDeb]("http://www.getdeb.net/app/Avant%20Window%20Navigator"). Remember to download all the .deb files and install them in the correct order (which I can't recall).

---

### Post by emarkd on 2008-01-30
Installing software in Linux is very different that in Windows for several reasons.  One is security, obviously.  Another is that Linux likes to keep ALL of your software up to date instead of just the OS.  

As far as Avant goes, use this guide:  [http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu](http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu)  The extra steps are required so that Linux can track changes to that software and keep you up-to-date.  You can also just download the .deb mentioned in the post above, but Linux will not be able to keep you up-to-date that way.  It's up to you which way you want to go.

---

### Post by B0whunt3r on 2008-01-30
even the deb doesn't work for me, says error in dependency libart 2
:(

---

### Post by emarkd on 2008-01-30
Did you try the tutorial I pointed to?:  [http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu](http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu)

---

### Post by B0whunt3r on 2008-01-30
i can't follow that either. I'm on dapper.

---

### Post by emarkd on 2008-01-30
Well, Dapper is not really designed to run the newest software, so you may not get it installed.  You can see [here]("http://wiki.awn-project.org/index.php?title=DistributionGuides") that AWN only claims to support Fiesty and newer.  That's not to say it can't be done...

Have you tried using Synaptic to install the missing dependencies that the .deb complained about?  You can use the search function to try and find what you're looking for.

---

### Post by B0whunt3r on 2008-01-30
I'm beginning to think this is over my head, this revelation after sitting here for 5 hours:(

---

### Post by emarkd on 2008-01-30
Don't give up!  Lots of people struggle at first because they're so used to doing it Microsoft's way.  Linux is different, not worse.  Quick question, why did you opt to go with Dapper over Gutsy?  AWN works in gutsy very easily.

---

### Post by B0whunt3r on 2008-01-30
it was the only one i could get the install cd to work correctly. is their a way to upgrade other than a complete reinstall?

---

### Post by mr_ed on 2008-01-30
Is there a reason you're using Dapper over Gutsy?

---

### Post by emarkd on 2008-01-30
I don't know if you can upgrade all the way from Dapper or not, but try

```
sudo apt-get upgrade dist-upgrade
```

Know that there are LOTS of changes between here and there and there's a very real chance that something could go wrong, especially if the Gutsy live CD didn't work for you.  A better choice would be to [download the Gutsy alternate CD]("http://releases.ubuntu.com/7.10/") and install it using the text-based installer.  Then after your install completes, you may have to fight a bit getting the video set up properly.  That's usually the biggest problem for most people.

What went wrong with the Gutsy Live CD the first time?

---

### Post by mr_ed on 2008-01-30
> **B0whunt3r said:**
> it was the only one i could get the install cd to work correctly. is their a way to upgrade other than a complete reinstall?

Yes, there is!

It'll take a while though.  The question that I have for someone else here is if Bowhunter should upgrade from Dapper to Gutsy immediately, or upgrade to Edgy, then Feisty, then Gutsy...

If you're not using evms, (and if you don't know what it is, you don't need it) remove it before doing the upgrade.

---

### Post by mr_ed on 2008-01-30
It looks like you should go through them one by one.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by B0whunt3r on 2008-01-30
looks like it's installing off the cd now. formatting partitions....

---

### Post by B0whunt3r on 2008-01-30
uh, no video. hard drive is blinking.

---

### Post by B0whunt3r on 2008-01-30
> **B0whunt3r said:**
> uh, no video. hard drive is blinking.

disregard, man that took a long time to start.

---

### Post by emarkd on 2008-01-30
Is this the Gutsy livecd we're talking about?

---

### Post by B0whunt3r on 2008-01-30
> **emarkd said:**
> Is this the Gutsy livecd we're talking about?

yes, i believe so. downloaded it from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by B0whunt3r on 2008-01-30
my god that was simple! do you ever feel like all the information out there on linux leads you on a wild goose chase?:)

---

### Post by emarkd on 2008-01-30
:)  Yeah, it's unfortunate that bad advice is floating around out there!  I'm glad you got it working.

---

### Post by CJ56 on 2008-01-30
Here's a useful guide to installing AWN -

[http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html](http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html)

I just used it myself to get AWN up and running. Just do what the guy tells you and it seems to work... :)

---

