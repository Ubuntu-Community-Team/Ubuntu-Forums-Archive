---
title: "[SOLVED] In need of advice/info on choosing a Distro."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-19
Now I know that choosing a distro can be a very individualistic process, I'm not looking for "the best" distro out there. Right now I've started testing the waters with Ubuntu, having come from a Windows only background. I'm running into a bit of a challenge with installing packages on ubuntu and I'm wondering if my dilemma can be remedied with a different distro, or if they're basically all the same.

Here's the deal, my dual-boot system (XPx64 and Ubuntu 7.10) are on a *completely* offline system. If I need to install software I download it from my online Windows box, copy it via Flash drive to my offline system, then do what I need to do. The catch that I'm running into with Ubuntu is that with each installation, even of the smallest package, I have to find and download sometimes *dozens* of dependency packages. So far the process goes something like this:

1) Try to install package, install denied because my system lacks a dependency.
2) Google the dependency and download it from [http://packages.ubuntu.com/gutsy](http://packages.ubuntu.com/gutsy)
3) Copy dependency package onto offline ubuntu system.
4) Install package; if package requires *more* dependencies (which it seems to happen often), return to step 2.

Installing my ATI driver took nearly three hours this morning.

For an *OFFLINE* linux system, is the above senario how most of the popular distos work, or is this rather specific to Ubuntu and Debian? Or do some distros work kind of like Windows where you snag the install and *poof* you're done?

I really REALLY REALLY want to ditch Windows as much as I possibly can, I'm hoping that being offline doesn't prove to be as much of a hassle as it's been thus far. I'd love to hear anyone's input and ideas on the matter. Aside from this "snag" I totally love Ubuntu and would like to keep my distro choice in a similar ball park... or something else that is "Coming from Windows" friendly.

Thanks everyone!

---

### Post by sumguy231 on 2008-01-19
All major distributions have software dependencies, that's just how things are done in the Linux world. To make things easier you would at least need a networked connection to another Ubuntu computer which could download the packages with apt and put them on the non-connected one, but I guess then you might as well network the first computer in the first place.

---

### Post by NullHead on 2008-01-19
If networking is an issue you might order a DVD of ubuntu. Also I bought 4 dvds of Debian and there is all the software and all dependencies that are in the repositories. That is one way ... the other way is to purchase a Wireless card for you're system if wiring a network cable is an issue.

---

### Post by asmoore82 on 2008-01-19
you seem to be creating your own headache ...

All modern "Desktop" linux distros will *want* to pull packages from an active network connection.
Online Package "Repos" and Automatic Dependency Solving are Groundbreaking Achievements;
take advantage of them to the fullest; get your Linux box Connected.

---

### Post by asmoore82 on 2008-01-19
Installing ATI Drivers *should be* less than(<) 2 seconds;
Don't believe the hype: you *Don't* need the absolute newest version,
the "Repo" edition works just fine and you get it working just by
"flipping the swith" with "Restricted Drivers Manager"(in "System -> Administration")
I went to the absolute news ATI drivers, tested out their Compositioning/AIGLX,
and then came right back the the older version that came with Ubuntu.

---

### Post by NullHead on 2008-01-19
asmoore82

You're simply not answering his question. He asker for a better way to solve his dependency  problem in an offline manner, not what he should be doing and what he should not be doing. If he wanted an easy way to get connected to the internet that he would've asked for one.

---

### Post by asmoore82 on 2008-01-19
> **toastysquirrel]is the above senario how most of the popular distos work,
or is this rather specific to Ubuntu and Debian?[/QUOTE]
[QUOTE=ME]All modern "Desktop" linux distros will want to pull packages from an active network connection.[/QUOTE]
[QUOTE=NullHead said:**
> You're simply not answering his question.

THREAD TITLE: "In need of advice" ... :-k

---

### Post by toastysquirrel on 2008-01-19
Play nice guys :)

Actually Nullhead and Sumguy provided some good insight as to the possible challenges I'll be running up against.  Plain and simple though, the offline box stays offline so I'm stuck looking for an offline solution.  By happenstance someone posted in one of my other threads a link to a site that may very well save by tush when it comes to updating and adding apps for my system by directing me to [Nonetdebs]("http://nonetdebs.homeip.net/").  Sure it's more work then if the system was online, but it sounds infinitely better then the ordeal I went through yesterday.

---

### Post by NullHead on 2008-01-19
Still I recommend downloading or buying a DVD with you're software located on you're disk.

---

### Post by rosegarden78 on 2008-01-19
That'a a very interesting question.  I had the same problem with Edgy and Modprobe and BCM43xx wifi card.  I needed the BCM43xx package offline so I downloaded it.  Then I could activate wifi without going online - to get online with router - but now I see you need to download dependencies.

I'm on Gutsy now and installed Ubuntu first then sudo aptitude install kde.  I like having both options.  I'm not sure how one would obtain source code or software depencies only available online without ever going online and making a backup disk.

After the Great Oil Crash of 2003 begins to take effect, and Executive Orders are called to protect national infrastructure, I can see how your question may be of great concern.  While you still can, create the biggest, boldest and best dual-boot / triple-mega server whatever.  Your greatest concern in the near future will not be your dependencies but power generation, food, water and transportation.

---

### Post by rosegarden78 on 2008-01-19
You may also try adding XFCE from Synaptic.  Then select Session Type when you log in.  Once Xubuntu has started try pressing Alt-F2 then type Nautilus.  This will give you many features familiar in GNOME.  I'm experimenting with this because the XFCE desktop seems to be the cleanest and fastest of them all.  And I like the features of Nautilus.

---

### Post by philinux on 2008-01-19
I think this would help.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by aysiu on 2008-01-19
If you're off-line, I'd recommend Debian, as it has at least 14 CDs' worth of software.

---

