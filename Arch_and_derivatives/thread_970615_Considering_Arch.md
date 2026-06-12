---
title: "Considering Arch"
date: 2008-11-04
forum: Arch and derivatives
---

### Post by JohnFH on 2008-11-04
I've heard so much about Arch that I'm now curious, but I have a few questions as it seems a bit mysterious.  

1. Why do people like it so much?

2. I have a fully working (K)ubuntu (8.04) setup that I don't want messed with, but I have test machines I could use and my main machine is very capable of running VirtualBox machines.  Anyway, since I already have a fully working system, so can Arch provide anything more?

3. What disadvantages to using Arch are there?  

4. I need my PC for image processing and I have to have my monitor calibrated.  Will argyllcms package still work?  I've got it to work on Ubuntu.  What about closed source packages like Google's Picasa and Bibble Pro?

Sorry for the many questions.  Thanks!

---

### Post by Barrucadu on 2008-11-04
> **JohnFH said:**
> 1. Why do people like it so much?
Because you get to build up your system from scratch, so it really is *your* system. Because the package manager is great. Because our overlord looks like Skeletor. Because we like tacos! :D

> **JohnFH said:**
> 2. I have a fully working (K)ubuntu (8.04) setup that I don't want messed with, but I have test machines I could use and my main machine is very capable of running VirtualBox machines.  Anyway, since I already have a fully working system, so can Arch provide anything more?
Arch provides, in my opinion, much more understanding than Ubuntu, as you have to put it together yourself. You learn what the individual bits and pieces are for. And for some reason that's just really fun.

> **JohnFH said:**
> 3. What disadvantages to using Arch are there?
It takes a while to set up, and you're likely to do something wrong the first time unless you follow the beginners guide carefully. It's also more likely to be unstable than Ubuntu as it uses newer packages.

> **JohnFH said:**
> 4. I need my PC for image processing and I have to have my monitor calibrated.  Will argyllcms package still work?  I've got it to work on Ubuntu.  What about closed source packages like Google's Picasa and Bibble Pro?
I haven't tried, but I would imagine so.

---

### Post by rsambuca on 2008-11-04
I don't know why you wouldn't just try installing it.  It isn't a big deal to try other distros.  Read the wiki, and if it seems like something you would be interested in, try it.  If it doesn't sound like it is for you, then don't!  

I haven't used it, but argyllcms is v1.0.3.

---

### Post by chucky chuckaluck on 2008-11-04
i was unsatisfied with ubuntu as it no longer was the right distro for me. i had been progressively stripping everything off every installation. so, being somewhat of a minimalist and being pretty impatient, i was attracted to arch's promise of building up from scratch and its speed. while it is faster, i guess nothing is as instant as i'd like, but it's pretty close. the cleanliness of the distro, though, is what i'm very pleased with. while a lot of the package management is still a bit of a mystery to me, i still find it a joy to use. the guides for installation are fantastic. 

if you're happy with your kubuntu setup, i think you're less likely to find something better for you. i pretty much think people should switch if they have a reason, not just out of curiosity. i had a reason. i'm not so sure you do, if that makes sense.

---

### Post by JohnFH on 2008-11-04
Thanks everyone.  Yes that makes perfect sense.  I've decided to give it a go in VirtualBox just to see what it's like to satisfy the curiousity in me, but I'll keep Kubuntu as my main OS.  That means I can delve into Arch when time permits while at the same time always having a working system.

Speed isn't a big issue for me as my machine is a bit nippy already (3GHz dual core with 4Gb RAM), so the speed boost won't give me much I don't think.  

You Arch type people seem a happy bunch so I wouldn't want to miss out on the fun!

---

### Post by Rumor on 2008-11-04
I would give a very big +1 to what Chucky wrote. If you don't have a reason to switch, and you are happy with what you are running, don't switch.

That said, Arch runs very well in a virtual box, so if you were wanting to give it a whirl, I'd recommend that route first.

Very briefly:

1. Arch is a rolling release. Thus there are no large distro upgrades such as the jump from Hardy to Intrepid. Rather there are incremental upgrades as new versions of packages become available.
The package manager is stellar.
The control over your installation is second to none.

2. Arch can offer less overhead than the *buntus as it is only running what you specify on start up.

3. Sometimes there are hiccups with the incremental upgrades. These are more frequent if you enable the testing or unstable repos and maintain your system on the bleeding edge. Using the standard repos should avoid the vast majority of any such hiccups.

4. Picasa works very well in Arch. The argyllcms package is in the AUR, as is bibblepro, so I presume they will work fine for you as well.
```
aur/argyllcms 1.0.3-1
    An ICC compatible color management system with support for different colorimeter hardware
aur/bibblepro 4.10.1-2
    Professional Workflow and RAW Conversion

```
As a rule, if a package works in one distro, it will work or can be made to work in another.

But if you are happy with what you are running, stick with it until you have a need for something else.

---

### Post by SomeGuyDude on 2008-11-04
> **JohnFH said:**
> I've heard so much about Arch that I'm now curious, but I have a few questions as it seems a bit mysterious.  

1. Why do people like it so much?

It's the feeling of control, for one. Plus the rolling release makes so much more sense than the six-month cycle. The fact that I never have to do an "upgrade" is fantastic.

> 2. I have a fully working (K)ubuntu (8.04) setup that I don't want messed with, but I have test machines I could use and my main machine is very capable of running VirtualBox machines.  Anyway, since I already have a fully working system, so can Arch provide anything more?

Speed, a learning experience, if you're big on saving system resources Arch is excellent.

> 3. What disadvantages to using Arch are there?  

Things break sometimes, and if you're not big on changing settings via a text editor you might not enjoy the process.

> 4. I need my PC for image processing and I have to have my monitor calibrated.  Will argyllcms package still work?  I've got it to work on Ubuntu.  What about closed source packages like Google's Picasa and Bibble Pro?

If it worked in Ubuntu, it should work in Arch. The pacman repos plus the AUR provides TONS of software.

---

### Post by handy on 2008-11-04
***@JohnFH:*** Even if after playing with it in VirtualBox you decide it is not for you, I expect that you will be really glad that you had the Arch experience, just for the fun of building it up & for the education that you will gain through having had the experience.

---

### Post by JohnFH on 2008-11-04
I really like the idea of the rolling release.  Right now I'm using Kubuntu 8.04, not 8.10 and hence not KDE 4.X.  I've got a nicely configured system and can't be bothered upgrading, but when I need to upgrade (Kubuntu 8.04 is not an LTS release) I may consider switching to Arch.

I've just installed it on VirtualBox along with KDE 4 and I can see what you mean.  It does take a little extra configuring but it isn't that difficult to be honest.  My first impression of it is good but I still think I'll stick with Kubuntu for the time being simply because I haven't got the time to reconfigure everything from scratch again.  

Handy I think you're right, although I haven't decided against it completely.

---

### Post by mojoman on 2008-11-05
I don't really consider myself an Arch user but I do keep it on my spare laptop. It's freaking ancient and Arch runs pretty good on low specs while still providing usability. I'd say that the configurability is great but a more accurate description would probably be that it comes unconfigured instead, as most distros do, with a standard or default configuration. Just about any distro is just as configurable, it just takes more time and effort to remove the default crust on some of them. With Arch, you're not gonna end up with the default just because you're lazy because, well,  there isn't much of one. The package manager is another strength I suppose. Coming from Debian I'd say my expectations are pretty high in this area but Arch didn't at least make me disappointed. The availability of packages is not a strenght. Unless you're willing to be dependent on AUR packages, and theses aren't always that well polished, you're going to have a slimmer choice of packages available. Installation and configuration was a bit different then Debian and Debian based distros (which is my usual poison) but it wasn't hard and I got a working system the first time around within an hour or so.

---

### Post by SomeGuyDude on 2008-11-05
**JohnFH**, I don't think many Arch users stick with it after their first foray. It took me four or five before I settled. Just keep it on the back burner for a while.

---

### Post by handy on 2008-11-05
I loved Arch from the first successful install.

---

### Post by SkonesMickLoud on 2008-11-06
If you're really interested in Arch, try installing and setting it up on a spare partition, or make some space for one.  Then, when/if you decide to come on over to the dark side (believe it or not, we DO have cookies), you can just move the install over, change a few text files around, and you're good.

This way, you can keep your current Kubuntu install.

---

### Post by JohnFH on 2008-11-06
> **SkonesMickLoud said:**
> If you're really interested in Arch, try installing and setting it up on a spare partition, or make some space for one.  Then, when/if you decide to come on over to the dark side (believe it or not, we DO have cookies), you can just move the install over, change a few text files around, and you're good.

This way, you can keep your current Kubuntu install.

It's not quite that simple.  I don't have a spare partition unfortunately so creating space for one is something else I would have to do, besides the fact I hate having extra partitions that I need to allocate space to.  Combine that with reprofiling my monitor (takes a loooong time) and it's not a trvial task.  

I suspect I will move to Arch eventually, but only when I feel I need to and that's not today.

---

### Post by rsambuca on 2008-11-06
> **JohnFH said:**
> I really like the idea of the rolling release.  Right now I'm using Kubuntu 8.04, not 8.10 and hence not KDE 4.X.  I've got a nicely configured system and can't be bothered upgrading, but when I need to upgrade (Kubuntu 8.04 is not an LTS release) I may consider switching to Arch.

If you are comfortable staying with older versions of software like this, then I think perhaps there are better alternatives for your needs than Arch.

---

### Post by SomeGuyDude on 2008-11-06
> **rsambuca said:**
> If you are comfortable staying with older versions of software like this, then I think perhaps there are better alternatives for your needs than Arch.

I think his point was more that he didn't want to do a full system upgrade, so the fact that Arch has no "new version" releases every 6-12 months is appealing. I have to say I feel the same way. There are lots of advantages.

One is that, duh, there's only one "version" of the system. You don't need to burn new CDs every six months. I just have the FTP install disc on hand and I'll never have to make a new one.

Two is that you get new stuff sooner, obvious.

The third is the neatest, which is that if a slightly buggy element comes down the pike, it's all by itself. Often a new version of a full distro upgrade comes along and a whole bunch of it isn't perfected, so when a users' system isn't working right they just blame the "new version" because SO MUCH is going wrong. In rolling release, thanks to the lack of a big bucket of upgrades all at once, each package can be fixed and updated in its own schedule.

---

### Post by chucky chuckaluck on 2008-11-06
[QUOTE=SomeGuyDude]The third is the neatest, which is that if a slightly buggy element comes down the pike, it's all by itself. Often a new version of a full distro upgrade comes along and a whole bunch of it isn't perfected, so when a users' system isn't working right they just blame the "new version" because SO MUCH is going wrong. In rolling release, thanks to the lack of a big bucket of upgrades all at once, each package can be fixed and updated in its own schedule.[/QUOTE]

really good points there, dude. full, regular upgrades bring in the completely unnecessary concern of a deadline. just release things when they're ready, i say.

---

### Post by JohnFH on 2008-11-06
Indeed.  You only need to have a look at all the threads like "Intrepid broke my PC" and "Do you think Intrepid was rushed?" etc, to see one of the benefits of a rolling release.

After playing around with it on a VirtualBox image, it looks like I'm sold on the Arch idea.  Wikipedia is quite informative on the differences between the Linux distributions.  Apparently Arch has approx 15000 packages in the repositories compared to Ubuntu's 23000.  That's a big difference but not big enough to scare me away.  Can .deb files be installed on Arch?

---

### Post by sub2007 on 2008-11-06
Arch doesn't have -dev packages like Ubuntu has. Often Ubuntu will have the main package and then a bunch of -dev and -lib packages which you don't have in Arch - you generally get just one package. That helps to explain why Ubuntu has larger repositories. Personally I haven't noticed them to be much smaller, in fact they often have packages that aren't in Ubuntu's.

Arch also has an enormous user created repository called AUR ([http://aur.archlinux.org](http://aur.archlinux.org)) which, whilst is unsupported, you can get nearly anything from there. It currently has over 10,000 packages (some of which are the same or newer versions of the packages in the main repositories) which are all maintained by members of the community (which I think is one of the huge selling points of Arch).

As for installing .deb files, I don't think you can but you won't need to. I've never found anything that isn't in either the repositories or AUR.

---

### Post by handy on 2008-11-06
> **SomeGuyDude said:**
> 
The third is the neatest, which is that if a slightly buggy element comes down the pike, it's all by itself. Often a new version of a full distro upgrade comes along and a whole bunch of it isn't perfected, so when a users' system isn't working right they just blame the "new version" because SO MUCH is going wrong. In rolling release, thanks to the lack of a big bucket of upgrades all at once, each package can be fixed and updated in its own schedule.

Well, it can be somewhat less tidy & easy than that, as the not too distant kernel bug proved to many of us.

Once you become familiar with the process of downgrading packages, & you happen to have NOT cleared your pacman cache it should not be too hard to get out of trouble once you know which package(s) is/are the cause of the trouble.

It is a pain if the bug removes access to the internet (where all wisdom resides) & you have to start accessing the internet via a liveCD in an effort to seek the wisdom of others experiences to find your way back to normality.  This can be quite a clumsy & time consuming process, certainly made easier for those of us with a 2nd web reference machine that's for sure.

---

### Post by rsambuca on 2008-11-06
> **SomeGuyDude said:**
> I think his point was more that he didn't want to do a full system upgrade, so the fact that Arch has no "new version" releases every 6-12 months is appealing. I have to say I feel the same way. There are lots of advantages.

One is that, duh, there's only one "version" of the system. You don't need to burn new CDs every six months. I just have the FTP install disc on hand and I'll never have to make a new one.

Two is that you get new stuff sooner, obvious.

The third is the neatest, which is that if a slightly buggy element comes down the pike, it's all by itself. Often a new version of a full distro upgrade comes along and a whole bunch of it isn't perfected, so when a users' system isn't working right they just blame the "new version" because SO MUCH is going wrong. In rolling release, thanks to the lack of a big bucket of upgrades all at once, each package can be fixed and updated in its own schedule.

I know what you guys are saying, but let's face it, if you are using one of the larger DE's such as gnome (like me!), then you are for all intents doing a full distro upgrade equivalent when the new packages roll out, complete with the bugs and potential inconsistencies.  The rolling release of single packages that you use is quite nice though, like Gimp, OO, etc.

---

### Post by Rumor on 2008-11-07
> **JohnFH said:**
> After playing around with it on a VirtualBox image, it looks like I'm sold on the Arch idea.  Wikipedia is quite informative on the differences between the Linux distributions.  Apparently Arch has approx 15000 packages in the repositories compared to Ubuntu's 23000.  That's a big difference but not big enough to scare me away.  Can .deb files be installed on Arch?

It is also a deceptive difference. You'll find some meta packages on Arch. For instance pacman -S xorg will install a group of packages.

Also, as has been noted, the "official" package count, if there is such a thing, does not include those in the AUR. 

Finally, if you do come across a program that is not in any of the repos, Arch gives you the tools to roll your own package for pacman to install and manage. 

That last is a very great strength. Rather than downloading the source for something and doing the "configure | make | sudo make install" shuffle with it, you can very easily build your own package. Later, if you wish to uninstall that program you compiled from source, you might have difficulty remembering where all its bits and pieces went. With the Aerch toolset, pacman -Rd removes it cleanly. Also, installing from source might cause a conflict with something down the line. Using the Arch toolset, you avoid that particular pitfall.

For my money, the [ABS]("http://wiki.archlinux.org/index.php/ABS") renders any differences in numbers of packages moot.

---

### Post by Barrucadu on 2008-11-07
> **Rumor said:**
> It is also a deceptive difference. You'll find some meta packages on Arch. For instance pacman -S xorg will install a group of packages.

They're not metapackages, but package groups. The difference is that you can do pacman -Rs xorg and choose which packages in the group to remove, unlike in Ubuntu where you have no choice as the metapackage depends on all of its components (apt-get remove ubuntu-desktop for example)

---

### Post by chucky chuckaluck on 2008-11-07
as long as it has the packages you want, i guess it doesn't matter how many it has. (true of any distro, of course.)

---

### Post by qpieus on 2008-11-07
> **handy said:**
> I loved Arch from the first successful install.
I'm with you on that. I put arch on my laptop and just love it. I seriously considering (OK, I've already decided :) ) that I'm replacing kubuntu 8.04 with arch on my main desktop pc. I don't want to run KDE4 yet, and with arch I can still use KDE 3.5.10.

---

### Post by mips on 2008-11-08
> **qpieus said:**
> I don't want to run KDE4 yet, and with arch I can still use KDE 3.5.10.

KDEmod 3.5.10 is also available.

---

### Post by qpieus on 2008-11-10
Thanks, mips. Yep, that's what I'm running. I originally installed kdemod 3.5.9., then it got updated to 3.5.10 a few weeks ago. Actually, that's a lie. I originally installed kde 4.1, then took that off and installed kdemod3 :)

When I install arch on my desktop I might try out vanilla kde to compare it to kdemod. What's your preference?

---

### Post by mips on 2008-11-11
> **qpieus said:**
> What's your preference?

KDEmod.

I use KDEmod4.1 on my desktop, the more testers the faster it gets better.
KDEmod3.5 is stable and you can trust it but I stopped using it when 4.1 came out.

A personal preference thing. Use what you prefer for whatever reason ;)

---

