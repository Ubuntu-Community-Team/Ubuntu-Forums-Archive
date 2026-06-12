---
title: "Will Ubuntu Run on This Old Laptop I Have?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2007-11-26
Hi everyone. I want to install Ubuntu 7.10 on an old IBM laptop. My question is , will it install and run? The specs of the system include:

[LIST]
[*]Intel Mobile Pentium II
[*]Neomagic MagicMedia256AV with 2.5MB
[*]64MB RAM
[*]10GB HDD
[*]DVD ROM Drive
[/LIST]

Thanks for the help and for reading my post.

---

### Post by icechen1 on 2007-11-26
I think there aren't enough RAM for Ubuntu or even Xubuntu.Try a smaller distro like Puppy or DSL.

---

### Post by ohjeez99 on 2007-11-26
It should boot from the disk, i tried running it on a slightly older laptop, but the problem i ran into was my bios was to old.  Make sure your bios is updated past the year 2000 and you should be fine with that aspect at least.  The ram does seem a bit low like icechen said, see if you can get a little more or try a different distro.

---

### Post by overdrank on 2007-11-26
+1 for puppy or DSL ( Damn small linux) 
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Crumpets and Jam on 2007-11-26
Do you know if gOS will run? I've heard that it only requires half of the hardware power that Ubuntu needs. Then again, I am a Linux noob. Any ideas?

---

### Post by meborc on 2007-11-26
i would go for dsl... but if you have spare cd's try out them all :)

---

### Post by irish_flu on 2007-11-26
The only thing I'd really be afraid of on that box is the 64MB of RAM.  Check what the minimum suggested requirements are for whichever distro you please, and if your RAM meets them there's every chance that the rest of your hardware probably will.

---

### Post by overdrank on 2007-11-26
> **Crumpets and Jam said:**
> Do you know if gOS will run? I've heard that it only requires half of the hardware power that Ubuntu needs. Then again, I am a Linux noob. Any ideas?

This is a quote from there site 
```
Official Answers
Actually Ubuntus requirements will be quite a bit more then ours. Some of the applications will require a bit more, but gOS should be able to run on a system with half the minimum requirements of Ubuntu just fine. The exact requirements have not been tested, but gOS should be much better for older systems, including Pentium II and possibly lower.
Answered by Nick Hughart
```

---

### Post by KCPokes on 2007-11-26
As been said, I'd be concerned with the amount of RAM.  Best you could do was Xubuntu, but I think you'd be disappointed even if it did run.  

I'd recommend Arch linux, but it does take a bit to set up.  It is as flexible as you could want.

---

### Post by ugm6hr on 2007-11-26
I'd recommend DSL too.

P2 & 64MB RAM will be painfully slow with Ubuntu (may be reasonable to try a minimal install).  PuppyLinux will be usable, but I would go with DSL.

---

### Post by Crumpets and Jam on 2007-11-26
Thankyou for the multiple answers. Does Damn Small Linux or 'DSL' have any kind of instant messenger client?

Cheers.

---

### Post by anemptygun on 2007-11-26
Yes, it's called naim

[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)

If you like ubuntu, I would try fluxbuntu. It is much lighter that xubuntu and has the same interface as DSL.

---

### Post by Crumpets and Jam on 2007-11-26
> **anemptygun said:**
> Yes, it's called naim

[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)

If you like ubuntu, I would try fluxbuntu. It is much lighter that xubuntu and has the same interface as DSL.

Thanks. I really like the look of Fluxbuntu. I might just have to try all of these distributions.

---

### Post by linuxlizard on 2007-11-26
pcfluxboxos tinyflux

Not sure if your ram is too small. 128 would be better, but it's worth a try as it isn't heavily modified like dsl and has extensive software repositories and synaptic, like ubuntu, but not quite as large- still very large though.

[http://tinyme.mypclinuxos.com/forums/index.php?PHPSESSID=869a80bc13cfda67b7e8430040541bd4&topic=1403.0](http://tinyme.mypclinuxos.com/forums/index.php?PHPSESSID=869a80bc13cfda67b7e8430040541bd4&topic=1403.0)

And yes, dsl has instant messenger software- gaim I think.

---

### Post by louieb on 2007-11-26
A great places for Linux on a Thinkpad [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")
And for everything else ThinkPad  [ThinkPad Forum]("http://forum.thinkpads.com/")
Getting more ram for those older ThinkPads is an inexpensive option.

---

### Post by SunnyRabbiera on 2007-11-26
tinyme is an awesome choice, so is damnsmall

---

### Post by ugm6hr on 2007-11-27
> **Crumpets and Jam said:**
> Thanks. I really like the look of Fluxbuntu. I might just have to try all of these distributions.

I don't think Fluxbuntu will work.

It only comes with a LiveCD, so needs more RAM to install than Xubuntu (from AlternateCD)!

---

### Post by rsambuca on 2007-11-27
> **Crumpets and Jam said:**
> Hi everyone. I want to install Ubuntu 7.10 on an old IBM laptop. My question is , will it install and run? The specs of the system include:

[LIST]
[*]Intel Mobile Pentium II
[*]Neomagic MagicMedia256AV with 2.5MB
[*]64MB RAM
[*]10GB HDD
[*]DVD ROM Drive
[/LIST]

Thanks for the help and for reading my post.

A [minimal Ubuntu installation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") will run on that.  If you follow the guide it gives instructions, incuding the exact procedures and code to install a minimal installation with GUI and a complete lightweight system.
It is the actual installation time that will take a while on that machine.

---

### Post by Grey Box on 2007-11-27
I have tried with a 64mb laptop and my solution was to use Puppylinux. I had tried DSL which was OK, but puppylinux was very simple and robust, and quick. The user interface was surprisingly good for 64mb. 

I tried Ubuntu but it really didn't like the low memory situation.

---

### Post by wheredidrealitygo on 2007-11-27
I've had awesome luck running Puppy Linux on an old Compaq 1200 (~600mhz celeron, 60megs ram, 6 gig hdd). ICEwm is the window manager.

Ndiswrapper is included in it out of the box for wireless support, and packages are easy to install through .pet and .pup packages.

---

### Post by anemptygun on 2007-11-28
> **ugm6hr said:**
> I don't think Fluxbuntu will work.

I got fluxbuntu to work on an IBM of similar specs.

---

### Post by anemptygun on 2007-11-28
like rsambuca said, try this [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
That way you can just start with the minimal and go from there.

---

### Post by sleepingdragon on 2007-11-28
I'm also going to vote for DSL on this one. I found DSL to be surprisingly laptop friendly, and with a bit of gentle persuasion you can get the desktop to run in only 10Mb of RAM, and about 15Mb to browse the 'net, so 64Mb should be fine. I found Puppy worked well with at least 92Mb, but should go OK-ish on a diet of 64Mb, so long as you don't try to do too much at once. I think someone mentioned it earlier, DSL comes with ndiswrapper, which should help out with any form of integrated wireless in the laptop. Just my $0.02...

---

### Post by Kelvari on 2007-12-01
Since we're talking about minimum system requirements, I've gotten Ubuntu 7.10 installed via Live CD on systems with 190 MB RAM and a 466 MHz CPU.

Currently testing a 96-MB system, but I DO know that the Live CD will NOT boot on 64MB or under.

---

