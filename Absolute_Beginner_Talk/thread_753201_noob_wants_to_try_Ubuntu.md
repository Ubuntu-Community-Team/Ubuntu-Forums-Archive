---
title: "noob wants to try Ubuntu"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by smof on 2008-04-12
Hi everyone.

I am running XP on my laptop currently but have been thinking of trying Ubuntu (again, I used to have it on my old desktop but I had a bad experience!)

I don't have any problems with XP, I just want to try Ubuntu for the hell of it really, to see if it runs a bit quicker and I don't get the random Firefox crashes. I only really use this laptop for work, photos and internet, I am keeping XP on my desktop for games because I know linux is not so great at them. But I don't want to ditch XP straight away and get stuck not knowing how to work Ubuntu on my laptop. I have 12GB of my hard drive free and was wondering how I could install Ubuntu without getting rid of XP. I don't think it is split into separate partitions so is it possible? Sorry if that's more of a Windows question!


This is my hardware specs:

Fujitsu Siemens S Series Lifebook
1.7GHz Intel Pentium M processor
1 GB RAM 
TEAC DV-28E-C DVD/CD-ROM
Intel Pro Wireless 2200BG Network Card

I have read that Ubuntu can sometimes have issues with wireless connectivity but I checked a list of compatible cards and I think mine will be okay. But if anything else stands out as having known problems I'd be grateful to hear it.


I have been reading a lot of threads on here and looking at guides and FAQs on Ubuntu sites but it's a bit overwhelming when you first come into it, so I apologise if I'm asking really obvious questions.

---

### Post by Inxsible on 2008-04-12
You can have a look at these links to get you started on dual booting XP and Ubuntu

[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")     [Installing]("http://www.psychocats.net/ubuntu/installing")

12 GB will be quite less to do anything worthwhile, but you can still get a feel for the OS and later give it more space.

---

### Post by hyper_ch on 2008-04-12
use first the desktopcd... it's a life cd and you should see if video card, wifi aso are working... if they do, then you may consider dualbooting.

---

### Post by kellemes on 2008-04-12
> **smof said:**
> Hi everyone.

I am running XP on my laptop currently but have been thinking of trying Ubuntu (again, I used to have it on my old desktop but I had a bad experience!)

I don't have any problems with XP, I just want to try Ubuntu for the hell of it really, to see if it runs a bit quicker and I don't get the random Firefox crashes. I only really use this laptop for work, photos and internet, I am keeping XP on my desktop for games because I know linux is not so great at them. But I don't want to ditch XP straight away and get stuck not knowing how to work Ubuntu on my laptop. I have 12GB of my hard drive free and was wondering how I could install Ubuntu without getting rid of XP. I don't think it is split into separate partitions so is it possible? Sorry if that's more of a Windows question!


This is my hardware specs:

Fujitsu Siemens S Series Lifebook
1.7GHz Intel Pentium M processor
1 GB RAM 
TEAC DV-28E-C DVD/CD-ROM
Intel Pro Wireless 2200BG Network Card

I have read that Ubuntu can sometimes have issues with wireless connectivity but I checked a list of compatible cards and I think mine will be okay. But if anything else stands out as having known problems I'd be grateful to hear it.


I have been reading a lot of threads on here and looking at guides and FAQs on Ubuntu sites but it's a bit overwhelming when you first come into it, so I apologise if I'm asking really obvious questions.

Informative link.. [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
I don't use wireless so can't tell you how this card works on Ubuntu but I can't imagine you'll have much trouble getting your system running. Have you tried the livecd by the way?
The 12 Gb is enough to get a full fledged Ubuntu system for sure.

For some reason it's recommended to resize the NTFS (Windows) partition using a Windows-tool, although GParted (the Linux partitioner) can do it.
As long as you have created your 12 Gb free space you can have the Ubuntu installer do it's thing, it will install a bootloader (Grub) that normally will automatically add an entry for your Windows install, if not.. no worries, it's fixable so just ask for support.

Without wanting to scare you.. you have to realize things **can** go wrong, so think about creating backups of important files etc.. Preferably on some external source obviously.

Good luck, let us know in case you need assistance.

---

### Post by freesitebuilder on 2008-04-12
I switched about 18 months ago, though I'm still dual-booting. Make sure you defrag (I had to defrag twice to move all my XP stuff to one part of the drive) before partitioning.

Some sites I find useful as a beginner:
[http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder](http://memo.yoono.com/buzzlog/links.jsp?login=freesitebuilder)

I'd recommend having a separate Home partition - I repartitioned afterwards, but it's easier to do it at the beginning.

Have fun, and welcome!

---

### Post by Jon Monreal on 2008-04-12
> **smof said:**
> Hi everyone.

I am running XP on my laptop currently but have been thinking of trying Ubuntu (again, I used to have it on my old desktop but I had a bad experience!)

I don't have any problems with XP, I just want to try Ubuntu for the hell of it really, to see if it runs a bit quicker and I don't get the random Firefox crashes. I only really use this laptop for work, photos and internet, I am keeping XP on my desktop for games because I know linux is not so great at them. But I don't want to ditch XP straight away and get stuck not knowing how to work Ubuntu on my laptop. I have 12GB of my hard drive free and was wondering how I could install Ubuntu without getting rid of XP. I don't think it is split into separate partitions so is it possible? Sorry if that's more of a Windows question!


This is my hardware specs:

Fujitsu Siemens S Series Lifebook
1.7GHz Intel Pentium M processor
1 GB RAM 
TEAC DV-28E-C DVD/CD-ROM
Intel Pro Wireless 2200BG Network Card

I have read that Ubuntu can sometimes have issues with wireless connectivity but I checked a list of compatible cards and I think mine will be okay. But if anything else stands out as having known problems I'd be grateful to hear it.


I have been reading a lot of threads on here and looking at guides and FAQs on Ubuntu sites but it's a bit overwhelming when you first come into it, so I apologise if I'm asking really obvious questions.
The laptop I am currently using has a Intel Pro Wireless 2200BG Network Card and it's working just fine as you can tell from me being able to post this. It didn't need any modifications or the use of ndiswrapper.

Anyways, the problem I have been hearing about lately is sound issues (no pun intended).

You could try the LiveCD or LiveDVD to see how well everything works first.

I hope everything goes well for you.

---

