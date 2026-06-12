---
title: "Tiny Core vs. Puppy vs. Crunchbang - Which is the best lightweight Linux distro?"
date: 2011-12-05
forum: Any Other OS
---

### Post by TeamRocket1233c on 2011-12-05
Hey there! After reading some stuff on Tiny Core, Puppy, and Crunchbang, I'm a little curious as to what you guys think.

Which of the three lightweight distros is the best, Tiny Core, Puppy, or Crunchbang? :)

Thanks! :)

---

### Post by jjex22 on 2011-12-05
If you want an install to function as a normal distro, but lightweight - crunchbang; being based on ubuntu, there's little comparison - great package support, very stable, and truly small YMMV, but mine is 112MB ram booted, seldom exceeds 300mb on my machine doing the usual's. I personally use it as a host platform for testing OS's in VMWare and VirtualBox because of it's small footprint.

Puppy is a great tool, and it can be really good for speeding up pc's if you open and close applications a lot, or read a lot from disk, because it loads completely into ram. It's also great for netbooks and portables, because of this feature (it doesnt, by default write to the disk until you shut down) as it gives even longer battery life by reducing HDD read/writes. Puppy I also very useful for making edits - it can unmount all partitions and swapoff - I use it to stay online whilst creating a HDD image, and for my netbook on long train journeys!

The puppy 5.x versions also containg Ubuntu code to support .deb packages, though I must warn you adding packages is often where puppy falls down - whilst crunchbang is just a case of add the dependancies, it really isn't a rare occasion where applications fail to install properly under puppy (under Wary I've had quite a few issues with Chrome.) I don't recommend Puppy myself for a full time distro - for one there's no user account or sudo, so you're running as root - which can be dangerous. You are also missing a lot of tools -(at the end of the day it's less than 400MB - well under a 10th of Crunchbang.

I've personally not used Tiny Core in about a year - not tested the current release, but I see it more of a tool than an OS, it's just too small for anything other than specific tasks IMHO. I have a lot of respect for it - a bit like quirky puppy - a realy achievement of how small you can go; but at a price.

Those are just my personal experiences with them, yours may vary, but I'd recommend Cruchbang for daily OSing, Puppy as a tool that also lets you keep working whilst using it (and as a travel OS), But tiny core, in my expereince is a case of look in aww... but it's not really meant to be a desktop OS - so it depends on your needs.

---

### Post by TeamRocket1233c on 2011-12-05
Cool. I've been somewhat considering lightweight distros in general as although full-blown distros like Debian, Ubuntu, or Fedora are great on modern hardware, a lightweight distro such as Crunchbang or Puppy would be snappier and use less resources. 

That and also, the current Crunchbang's based on Debian so you can use the Debian repositories with no problem in it, whereas Lucid Puppy 5.2.8's Ubuntu-based, which means you can probably use the Ubuntu repositories in it.

Also, Tiny Core would probably perform best on netbooks as it uses the least resources of the three distros, as its ISO's only 10 megs in size, whereas Puppy's is 128 megs in size and the current Crunchbang ISO's 512 megs.

Plus Tiny Core looks kinda like a stripped-down OSX in a way.

You can also probably set Tiny Core up how you want it if you do a LOT of hacking... And both Tiny Core and Puppy would be great travel OSes as you could set up a flash drive with them and have plenty of disk space left over on the particular Linux drive you set up using those two distros.

And Tiny Core would be best for setting up in a beginner's virtual machine due to its size.

So in other words, Debian, Ubuntu and its variants, or Fedora: best for desktop usage as desktops are generally more powerful than laptops, whereas Crunchbang: better for laptops as you can still have a half-decent desktop on a laptop with no problem. Now Puppy and Tiny Core: best for netbooks as they can have a relatively easy to use desktop, with Puppy's desktop boasting a Windows 95/98/2000 look and feel, and Tiny Core's having a dumbed-down OSX look and feel. That and they use the least resources of any currently supported distro, and with netbooks, ease of use and low resource usage is everything.

In addition, for setting up a Linux drive, 32-gig or 64-gig is a safe size to go for, whether you're using a lightweight distro or a full-size one.

---

### Post by jjex22 on 2011-12-05
If you like the idea of an OSX style dock, you  can add them to pretty much any DE nowadays - they don't all need compositing either, so their footprint isn't huge. 

[This]("http://penguininside.blogspot.com/2009/09/10-panel-dock-applications-for-your.html") guide is for openbox - so crunchbang.

At the end of the day, you can set up any linux to do whatever you want really - puppy even allows you to create 'pupplets' from it. You can most definitely get tinycore up to a stable, full use light distro - but I warn you it can be a lot of work. If you liked the idea of creating a custom system exsactly to your needs, I'd also say take a look at gentoo - It was my second ever distro after Fedora Cambridge, and I learnt a hell of a lot building it - you wont get it as tny as tinycore - nothing really is- but then I can't see the advantage of being that small - there's just too much missing for my needs. It is worth baring in mind you almost instantly get a low resource distro just by changing your DE to something like flux/openbox or LXDE/Enlightenment if you like it less minimal.

---

### Post by TeamRocket1233c on 2011-12-05
:)

---

### Post by IWantFroyo on 2011-12-05
CrunchBang is my favorite, but it doesn't really count as a lightweight distro. I would put it at a 'medium'. It's still Debian, and it has Flash and other things. It's still lighter than most distros, though.

My vote for the lightest distro, since I haven't used PL in a long time and never bothered with TC, goes to Arch. As long as you don't install anything graphical, your computer will fly.

---

### Post by |{urse on 2011-12-05
Out of the 3 for a desktop I'd say crunchbang. All the reason why I did not choose puppy or tinycore were already listed above by someone else.

---

### Post by TeamRocket1233c on 2011-12-05
Coolios! Might go ahead and go with Debian for a full-blown distro, because I really like the GNOME that it ships with, having used it before in Ubuntu 9, and Crunchbang for a lightweight distro for running on either full-fledged laptops or desktops, Puppy for a netbook distro, and Tiny Core for a USB flash drive distro.

---

### Post by wolfen69 on 2011-12-05
> **TeamRocket1233c said:**
> :)

Insightful. :P

Tiny Core, I think is good for tinkerers and specific needs users.

Puppy is great for very low spec pc's and thumbdrives/recovery tool.

Crunchbang is a more full service distro with a minimal interface.

That's the end of my in-depth review. ;)

---

### Post by LinuxFan999 on 2011-12-05
Another option is to do a minimal install of Ubuntu, then install a lightweight Desktop Environment, like LXDE or IceWM. If you don't want to do very much tweaking, Crunchbang and Puppy are good options to.

---

### Post by TeamRocket1233c on 2011-12-05
Good ideas guys.

---

### Post by wolfen69 on 2011-12-05
> **LinuxFan999 said:**
> Another option is to do a minimal install of Ubuntu, then install a lightweight Desktop Environment, like LXDE or IceWM. If you don't want to do very much tweaking, Crunchbang and Puppy are good options to.

Doing a minimal install is always fun too. It can be *very* fast and efficient. But for an ancient pc, I might opt for 10.04 or earlier.

---

### Post by TeamRocket1233c on 2011-12-05
Doing a full-blown install is always better though, and ancient hardware isn't the only hardware that lightweight distros are good for. They'll also fly on modern hardware.

And speaking of Tiny Core, another good example of a real minimal OS that would be perfect if you wanna do a lot of tweaking/hacking to get it set up, although not Linux, is OpenBSD.

---

### Post by jjex22 on 2011-12-05
> **TeamRocket1233c said:**
> Doing a full-blown install is always better though, and ancient hardware isn't the only hardware that lightweight distros are good for. They'll also fly on modern hardware.

And speaking of Tiny Core, another good example of a real minimal OS that would be perfect if you wanna do a lot of tweaking/hacking to get it set up, although not Linux, is OpenBSD.

I wouldn't say the main 3 BSD flavours (Free, Open, Net) are designed to be minimal in the same way puppy/core are - they are meant to be full featured, they just start you off at the CLI like Arch, Gentoo, minimal installs of Ubuntu, Fedora, debian etc. I do think that building your own system from a minimal install is a really good idea, though I take back my advice of Gentoo; that's just where I started - it's more of a pain to maintain than others- I'd go with the advice of IWantFroyo or wolfen69 and start with Arch or minimal Ubuntu, but to be honest you can use any distro or BSD that lets you install a minimal environment - if you wanted BSD, I'd suggest that FreeBSD has the most active support forums as well as the most packages of these systems.

Edit: maybe not take back Gentoo - it is crazy configurable, but the learning curve is steep, I'd say recommend with a warning - it was the first text install I did and it took me 2 weeks of evenings and weekends, with countless start overs - I got to that stage where I could get all the way through to compiling my kernel without looking at the manual 'coz I messed up so many times. And it does give you the most control with USE flags - I loved it for a long time, but it does take a lot of work to maintain, so, my warning is it's fantastic for learning how GNU/Linux (and all *nix) systems work, and for getting everything how you want it, but one day you will delete it!

---

### Post by TeamRocket1233c on 2011-12-05
Hmm...

---

### Post by wolfen69 on 2011-12-05
Best thing to do is try a lot of things and learn as much as you can. Nothing can take the place of experience.

---

### Post by TeamRocket1233c on 2011-12-05
Agreed.

---

### Post by daftlad on 2011-12-06
I have been using Bodhi on my old laptop and am getting to like it a lot. It uses the Enlightenment desktop and is based on ubuntu.


[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by TeamRocket1233c on 2011-12-06
Sweet!

---

### Post by Paddy Landau on 2011-12-06
On the other hand, if you want to load an Ubuntu-based distro and just "go" without having to tweak, why don't you look at [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"). It's lightweight -- not as light as Puppy or Tiny, obviously -- but good for smaller spec machines, and is fully part of the Ubuntu family.

---

### Post by snowpine on 2011-12-06
My vote is CrunchBang. :)

I was surprised not to see SliTaz on your list, I much prefer it to Puppy.

---

### Post by TeamRocket1233c on 2011-12-06
That's cool. I just hadn't read too much into SliTaz.

---

### Post by lykwydchykyn on 2011-12-06
I like tinkering with tinycore, and I've installed slitaz numerous times just checking it out.

But for actual usage, I just usually install a minimal Debian install and build a lightweight desktop from scratch.  If you have enough RAM, even an old PII will do well.

---

### Post by TeamRocket1233c on 2011-12-06
That would also work with a perfectly modern, adequately powered system too, and it would boot and in general work faster than say Windows Vista or Windows 7, although both are relatively fast on modern hardware.

But Tiny Core is perfect if you wanna do a lot of hacking to get your OS set up, and OpenBSD is the same way.

---

### Post by TeamRocket1233c on 2012-02-01
BTW, I'm running Crunchbang on my PC currently, and it runs great on it, despite my hardware being freaking ANCIENT!!

Might go ahead, if I manage to get a fairly recent PC, something with a Pentium 4 preferably, and put Crunchbang on that, as if it'll run on a PII~266-based PC with 128 megs of RAM with no problem, it'll run laps around Windows XP, Vista, or 7, or even Ubuntu, Debian, or Fedora on a P4~2GHz-based PC with about a gig or two of RAM.

Also, considering using Puppy 5.2.8 to rehabilitate an old Gateway PC from 2000 that has been considered dead for a while due to the Windows 98 install that it shipped with originally basically dying, and that thing has 63 megs of RAM, and from what I read in Puppy's Wikipedia article, it's capable of running on 48 megs, and its CPU, a Celeron~433, should be plenty for Puppy.

---

### Post by KdotJ on 2012-02-01
My vote would go to ArchBang, as its what I use for a simple lightweight distro. Arch if you have the time (and patience!)...

---

### Post by TeamRocket1233c on 2012-02-01
OpenBSD's also a good choice if you have the time and patience.

---

### Post by andrew.46 on 2012-02-03
Another good 'lightweight' choice would be Slackware 13.37 with Fluxbox. Works nicely here on reasonably minimal hardware...

---

### Post by kazuya on 2012-02-03
Of those three choices, Crunchbang is the most feature-rich. But if you are looking for the best choice in terms of speed and functionality, none comes close to "Archbang"
 
It comes with openbox, flash, etc, and is ridiculously fast if you can get past using pacman -S packagename to install things. It uses considerably less RAM to run even when installed compared to any of the others. 
 
Vectorlinux and Salix (slack-based) are great alternatives as well. They are almost as fast as Archbang, but have the bonus of a graphical software package manager. 
 
Laptops where Lubuntu and Mepis antiX would run very slowly, archbang even similar DE runs significantly faster.

---

### Post by TeamRocket1233c on 2012-10-03
> **lykwydchykyn said:**
> I like tinkering with tinycore, and I've installed slitaz numerous times just checking it out.

But for actual usage, I just usually install a minimal Debian install and build a lightweight desktop from scratch.  If you have enough RAM, even an old PII will do well.

Hey, you could make Tiny Core plenty usable with enough tweaks. For example, starting off with an Openbox WM, and adding Tint2 as the panel, as well as whatever other software you wanna add, would add some serious usability points right there, considering TC already comes with a dock.

---

### Post by lykwydchykyn on 2012-10-03
> **TeamRocket1233c said:**
> Hey, you could make Tiny Core plenty usable with enough tweaks. For example, starting off with an Openbox WM, and adding Tint2 as the panel, as well as whatever other software you wanna add, would add some serious usability points right there, considering TC already comes with a dock.

It's hard to remember after eight months, but I'm pretty sure the usability of the desktop environment was not what was on my mind when I made that comment.

I would go with Debian for a system that I plan to regularly use mainly because of application support & availability, regular patches, documentation, larger community, hardware support, etc.

Nothing against TC or Slitaz -- they have their uses, and I've certainly put them to use -- but when you compare them to a mainline distro on those terms, there's just no contest.

I mean, hey, last time I checked TC didn't have emacs in its repositories.  That's a non-starter for me :D.

---

### Post by majabl on 2012-10-03
I had Puppy Linux and Lubuntu running very nicely on an old Celeron 633/384MB RAM I had. Puppy was much quicker to boot and in general use, but felt somewhat old fashioned in its interface and for love nor money I could not get it to recognise my dongle for wifi. With Lubuntu things were noticeably slower than Puppy, noticeably quicker than Xubuntu and Ubuntu, but still acceptable for general light computer use (web browsing and word processing).

---

### Post by sidzen on 2012-10-03
I'm curious -- has anyone tried the new [Absolute]("http://distrowatch.com/table.php?distribution=absolute") 14 on an old dinosaur?  I used it a couple years ago and found it very functional.  

My vote?  #! 10 i486.

---

### Post by TeamRocket1233c on 2012-10-04
> **lykwydchykyn said:**
> It's hard to remember after eight months, but I'm pretty sure the usability of the desktop environment was not what was on my mind when I made that comment.

I would go with Debian for a system that I plan to regularly use mainly because of application support & availability, regular patches, documentation, larger community, hardware support, etc.

Nothing against TC or Slitaz -- they have their uses, and I've certainly put them to use -- but when you compare them to a mainline distro on those terms, there's just no contest.

I mean, hey, last time I checked TC didn't have emacs in its repositories.  That's a non-starter for me :D.

My fave lightweight distro is always going to be Crunchbang though, both 'cause of Openbox, and 'cause it's Debian Stable under the hood.

---

### Post by kiyop on 2012-10-04
IMO, definitely, Debian, if you know how to configure lightweight environment with Debian.

Tiny Core vs. Debian -- Debian has more packages.
Puppy vs. Debian -- Debian is more secure, Debian has more packages.
Crunchbang vs Debian -- You can configure Debian more as you like.

I am not familiar with Gentoo.
I cannot manipulate Slackware well.

---

### Post by Elfy on 2012-10-04
Old thread closed.

---

