---
title: "Small Ubuntu"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-02
I wanted a small Ubuntu to fit on a 3 gig drive, and I'm logging the experience here to save someone else some time.

With Feisty, Canonical recommends 1.5 gigs of space for Xubuntu, 3 for Kubuntu, and 4 for Ubuntu.

*Kubuntu* 

First choice only because I already use a lot of KDE apps. For kicks I did mini.iso -> server -> kde-core -> kubuntu-desktop. I ended up with ~400mb of free space before eliminating unneeded apps.

All good, except for KNetworkManager issues that I eventually gave up on.

*Xubuntu*

My install stopped on partitioning errors. An online search found that's not uncommon, so I installed my old 6.10 Xubuntu first, then upgraded. I ended up with only ~200mb of free space before eliminating unneeded apps. I'm not sure why, and I never got it down to anything like a 1.5 gig install.

I found I didn't like Xubuntu, as much as I'd wanted to. The 7.04 version seemed like a feature-reduced Ubuntu without any speed or usability advantages.

*Ubuntu*

Surely there must be a way to install an app-reduced Ubuntu. I read psychocats, which is great fun but not quite what was needed. Then I noticed Edubuntu only requires 2.5 gigs -- perfect: an Ubuntu desktop with a smaller app load.

But while that downloaded, I found 'CustomUbuntu'.
[http://wiki.makethemove.net/index.php?title=CustomUbuntu](http://wiki.makethemove.net/index.php?title=CustomUbuntu)

I followed those instructions up to 'Fancy Stuff', then added an apt-get for synaptic. I ended up with 1.6 gigs of free space. *Very* nice.

It's pretty stripped, but it's recognizably Ubuntu. Nothing like the sort of difference there is between kde-core and kubuntu-desktop. It's Ubuntu, just with very few items in the Applications menu.

I've added a few "daily" items to my taste - like Opera, Konq, GQview, Bitstream & other fonts - and I still have 1.3 gigs of free space on a 3 gig drive.

So if you want to shoehorn in a Ubuntu on a secondary machine, have a look at this.


*Omission*

My install was a little exciting because I got network problems somewhere in the middle, so I had to install some items like gnome-terminal again afterwards. I'm still having the network issues but they're a lot like what was wrong in Kubuntu, so I don't think it's directly relevant to the CustomUbuntu install. I'll do a separate post asking about that if I don't have better luck figuring it out. It must be something to do with my hardware.

---

### Post by sirgogo on 2007-10-02
Wow, thats pretty cool. Are the read times fast enough though to boot from? Is it laggy?

A friend of mine tried this with Fedora Core, and it didn't work out too well-- it had tons of errors when starting up and wouldn't work with some systems (a real pain).
:popcorn:

---

### Post by HermanAB on 2007-10-02
If you wish to run off a memory stick, then nothing beats Puppy Linux.  It can run off a tiny 128MB memory stick quite nicely and anything bigger provides oodles of storage space.  It is also screamingly fast and has special modifications to avoid wearing out the memory stick.  You can also encrypt the stick, which is essential since those things are easy to lose.

So, yes, while you can run Ubuntu off a stick, it is not necessarily a good idea to do so - and it may be better to go with something that is made for the purpose.

Cheers,

H.

---

### Post by ofb on 2007-10-02
> **sirgogo said:**
> Wow, thats pretty cool. Are the read times fast enough though to boot from? Is it laggy?

It boots faster. 2 minutes compared to 3 minutes for the Kubuntu install, and 2 3/4 minutes for the full Ubuntu on my slightly faster main machine.

Near as I can figure it's a prefectly normal Ubuntu install with few apps. Most of what you usually have in Preferences and Administration is there. 

Perhaps the people who actually know what they're doing can confirm this?


HermanAB -- Yeah, Puppy Linux is the sauce for true minimum situations. It's a remarkable distro. 

What I was seeking here was a similar environment to KVM back and forth with. Box2 is mostly a backup for when Box1 is busy, and it'll get the ugly MS free fonts for testing websites on browsers.

I was surprised to shoehorn Ubuntu into the tiny old drive, so I thought I'd pass it on for people. But I wouldn't recommend going below the recommended 256MB of RAM as well. Really old hardware should definitely look at Puppy Linux.

---

### Post by ofb on 2007-10-19
Update: the upgrade to 7.10 via the Alternate CD was a disaster on this machine.

I don't have time to do a autopsy to find out if any of it is related to the custom install or the tiny drive. This is reminding me more of the upgrade from 6.06 to 6.10. I was one of unfortunates who wound up having to format and start fresh after that one.

But I want to mention that the small drive is a problem because you need about 1.4 gigs of free space, as the regular upgrade installs all the apps you didn't want.

Fluxbuntu 7.10 is out in a few days. That may be a much better idea for people interested in this sort of thing.
[http://fluxbuntu.org/](http://fluxbuntu.org/)

EDIT: I managed to salvage it while waiting for Edubuntu to download. With aggressive pruning I've got the install down to 2 gigs. All told, I don't think it's worth it and suggest Edubuntu for a low-app version of Ubuntu. I'm not sure  exactly  how much drive space 7.10 needs - that info hasn't been updated yet. Hopefully it hasn't climbed as much as the requirements for Ubuntu did.

---

### Post by ofb on 2007-10-25
UPDATE

I just did a fresh install of Edubuntu 7.10. After installing the Nvidia driver and allowing updating, there's 550 MB free on a 3.2 gig drive. 

Fire up Synaptic, enable the unselected Partners, Proposed, and Backports in repositories, then select 'Delete downloaded packages after installation', and update again: 560 MB free.

Note that it did need to download about 200 MB in packages to do that, so I think it's fair to say the minimum space requirement for Edubuntu 7.10 is 3 gigs. (Canonical hasn't posted the official System Requirements yet.)

I'll probably gain about 300-400 MB after pulling out the apps I don't want, and installing those I do. YMMV, certainly.

Performance is quite sparky after selecting None for visual effects.

---

