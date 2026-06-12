---
title: "small linux?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-04-02
OK, I need a small linux distro for my old laptop, preferably one which will just boot from the CD, so I wont need any HDD space.  Hopefully there is one with openoffice and a media player.  Any suggestons?

---

### Post by Cloudy on 2007-04-02
Damn Small Linux?

---

### Post by trent dillman on 2007-04-02
...

---

### Post by jgrabham on 2007-04-02
hmm considering it, but a bit too small, no openoffice.  (sorry being picky now aren't I)

---

### Post by justin whitaker on 2007-04-02
> **jgrabham said:**
> hmm considering it, but a bit too small, no openoffice.  (sorry being picky now aren't I)

There is a variant, NDSL or something, that has Open Office. You might also try one of the Puppy Linux variants which include Open Office.

---

### Post by Skrynesaver on 2007-04-02
> **jgrabham said:**
> OK, I need a small linux distro for my old laptop, preferably one which will just boot from the CD, so I wont need any HDD space.
So far so good I'd advise DSL 
>  Hopefully there is one with openoffice and a media player.  Any suggestons?OpenOffice just isn't small, it's a great application but it's not suitable for running off a CD on an old machine.  Which aspects of it were you hoping to use, DSL has Ted for word processing and Siag as a spreadsheet application, not as well finished or as featurefull as Open Office but excellent as lightweight alternatives.
XMMS is included as a media player

---

### Post by jgrabham on 2007-04-02
> **Skrynesaver said:**
> So far so good I'd advise DSL 
OpenOffice just isn't small, it's a great application but it's not suitable for running off a CD on an old machine.  Which aspects of it were you hoping to use, DSL has Ted for word processing and Siag as a spreadsheet application, not as well finished or as featurefull as Open Office but excellent as lightweight alternatives.
XMMS is included as a media player

does Ted open *.doc files?

---

### Post by Cloudy on 2007-04-02
Out of curiousity what are the specs on this laptop in question?

---

### Post by jgrabham on 2007-04-02
IBM thinkpad 600
300mhz cpu
2mb graphics
4gb HDD
224mb RAM
Win XP

---

### Post by Cloudy on 2007-04-02
Yeah, DSL or Puppy Linux ought to work fine on that. You could always also try Xubuntu.

---

### Post by cyberdork33 on 2007-04-02
DSL-Not is DSL with some other "features" but still maintains the small footprint.

---

### Post by Skrynesaver on 2007-04-02
> Originally Posted by **jgrabham **does Ted open *.doc files? 
No alas, rtf only though there is an included Office viewer to read Office files. You could of course install wv (DSL is Debian based so apt-get install wv) and translate to rtf.  I've been know in the dim and distant past when asked for a document in doc format to supply one as RTF and change the extension, Word opens it transparently.

---

### Post by kerry_s on 2007-04-02
If your that picky you can always go custom install of *ubuntu. :) 
I would go custom build up and put only what you want, it's so much easier then trying to use what someone made for the masses or there own needs. Take your time do a little research, make a list of the exact app's you want to use, make sure there in the repos, then do a server install and build away.

Net installers:

edgy-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

Feisty-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)


I would start with> apt-get install xorg gdm fluxbox synaptic
reboot
select fluxbox from the session menu and log in
open synaptic and build your perfect install.

---

### Post by jgrabham on 2007-04-03
> **kerry_s said:**
> If your that picky you can always go custom install of *ubuntu. :) 
I would go custom build up and put only what you want, it's so much easier then trying to use what someone made for the masses or there own needs. Take your time do a little research, make a list of the exact app's you want to use, make sure there in the repos, then do a server install and build away.

Net installers:

edgy-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

Feisty-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)


I would start with> apt-get install xorg gdm fluxbox synaptic
reboot
select fluxbox from the session menu and log in
open synaptic and build your perfect install.


yes, but i doubt i could get the internet on it.

I have deleted some files on the laptop, so I need a good distro about 1gb or smaller, any suggestions?

needs to run well on 228mb of RAM and a 300mhz pent II

---

### Post by Maestro23 on 2007-04-03
> **jgrabham said:**
> yes, but i doubt i could get the internet on it.

I have deleted some files on the laptop, so I need a good distro about 1gb or smaller, any suggestions?

needs to run well on 228mb of RAM and a 300mhz pent II

Distrowatch.com: [http://distrowatch.com/](http://distrowatch.com/)

Good luck.

---

### Post by kerry_s on 2007-04-03
> yes, but i doubt i could get the internet on it.

Okay, i'll bite. What's wrong with your internet?

This setup i'm using was a test install, i wanted a setup small enough for a cf card, but with all the basic features. I used mem=128 and built a install that was around 500mb, it took time but i did it. Now i'm running some heavier apps and have installed the office suites, so i'm running it as my normal desktop. A little tip, the online office suites work if you want to save the space. Hmm, i wonder if it's still good at 128mb. I be back.

Wow so weird, with the recent kernel updates it won't even boot with mem=128, it just gives a stack error and locks up.

Okay my bag, i forgot the "m". I couldn't use mem=128m because i already deleted my swap so it was to slow. Here's a pic with mem=256m, i can't change my cpu so it's really hard to tell if yours will be slow, but mine runs fine and is just as speedy as with full ram(1024).

---

### Post by lyceum on 2007-04-03
Fluxbuntu will be out soon. I have played with the beta, it is very cool and light. Does not have OOo, but once you get it on the PC you can install it with apt-get.

---

### Post by AMDAthlonX2 on 2007-04-03
Mandriva mini is nice and small for a low end PC

Also try Koppinix linux, it boots directly from the CD

---

### Post by nonewmsgs on 2007-04-03
> **lyceum said:**
> Fluxbuntu will be out soon. I have played with the beta, it is very cool and light. Does not have OOo, but once you get it on the PC you can install it with apt-get.

what is OOo? object oriented operating?  i know OOP.  

puppy i love.  anytime i want to "just browse" with one of my laptops to check my email, netflix, and not do any major computing i use it.  although it doesnt come with open office i installed it and it saves to a single file on the hard disc so it doesnt bother your normal OS.  it does come with abiword which can read doc files but for some reason doesnt start initially configured with the dictionary thing.  grrrr. that reminds me. i have to figure out how to do that.:guitar:

---

### Post by Dual Cortex on 2007-04-03
> **nonewmsgs said:**
> what is OOo? object oriented operating?  i know OOP.  

puppy i love.  anytime i want to "just browse" with one of my laptops to check my email, netflix, and not do any major computing i use it.  although it doesnt come with open office i installed it and it saves to a single file on the hard disc so it doesnt bother your normal OS.  it does come with abiword which can read doc files but for some reason doesnt start initially configured with the dictionary thing.  grrrr. that reminds me. i have to figure out how to do that.:guitar:


[http;//en.wikipedia.org/wiki/OOo]("http://en.wikipedia.org/wiki/OOo")
> OpenOffice.org (abbreviated OOo) is an open source office suite. It is available for many different platforms, including Microsoft Windows, Unix-like systems including Solaris and Linux, and Mac OS X. It is intended to be compatible with, and compete with, Microsoft Office.

An abbreviation of openoffice.org

---

### Post by jamesjeffries1 on 2007-04-03
goto [http://linuxmigration.tk](http://linuxmigration.tk) for help switching to linux
try puppy linux its great and you dont even need to install it on your harddrive

---

### Post by Doug11 on 2007-04-04
I have an old laptop Pentium 266 with a 4gig HD and only 64 MB of ram. Is there any Linux distro that will run on this? I have tried a few old versions of puppy and DSL but they wuld hang on the install. Any others I might want to consider?

---

### Post by benner on 2007-04-04
i'm trying to get a dell 200mhz laptop with 32MB ram going.  couldn't install puppy or dsl-n.  dsl had some weird video problems.  i too would like any good tip on this.  i will take a look at sarge though.

---

### Post by lyceum on 2007-04-04
> **nonewmsgs said:**
> what is OOo? object oriented operating?  i know OOP.  

puppy i love.  anytime i want to "just browse" with one of my laptops to check my email, netflix, and not do any major computing i use it.  although it doesnt come with open office i installed it and it saves to a single file on the hard disc so it doesnt bother your normal OS.  it does come with abiword which can read doc files but for some reason doesnt start initially configured with the dictionary thing.  grrrr. that reminds me. i have to figure out how to do that.:guitar:

Sorry, OOo is short for OpenOffice.org.

---

