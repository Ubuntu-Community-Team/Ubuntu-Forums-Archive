---
title: "Creating a home partition for a fresh install"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-12-09
I've read from numerous sources that there seems to be a lot less problems when doing a fresh install instead of an upgrade. I don't want to have to reinstall my applications or reconfiqure all my settings so will creating a home partition faciliate that or not (i know an upgrade will)?

---

### Post by cotcot on 2007-12-09
Not more or less than a reinstall without separate home supposing you do not reformat the partitions.

---

### Post by Myglaren on 2007-12-09
Yes.  Prior to the one-before-last install I used Gparted to create a /home partition then installed Feisty.  When I upgraded to Gutsy, all my personal stuff remained the same, down to automatically logging me in here.   Did the same with the old dual-boot machine and that is the same.

---

### Post by intense.ego on 2007-12-09
So what are the advantage of an upgrade as opposed to creating a home parition and fresh installing?

---

### Post by Incense on 2007-12-09
Yes a home part will keep all your data and settings safe if you need to reinstall ubuntu, or even install another distro. It's really the only way to use Linux IMO. See the link below if you do not already have a home part. 

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Myglaren on 2007-12-09
Well, it was partly experimental.

I was aware of the possibilities for this from reading this forum, I had a 32bit install of Feisty that was cracking up a bit so in preparation for the release of Gutsy I wiped the machine and repartitioned, installed 64 bit Feisty.

Sad to say it wasn't much better once it setled in but the Gutsy CDs were on their way so I hung on ready to do a clean install, something I have always done in the past.

The CDs arrived but I was a bit too occupied with other stuff to install Gutsy immediately.  In the interim period I carried on using the machine (this one) and installing updates as they appeared.

After one set of updates, update manager offered an online upgrade to Gutsy so I thought "What's the harm, I'm going to install it anyway, if it all goes horribly wrong, I have the CDs here."  So opted for the upgrade.  It took (IIRC) 2 hours to download and an hour and a half to install, followed by a reboot that took all of fifty seconds.

I have been very pleasantly surprised, everything works perfectly now and it was a very simple and painless procedure, particularly compared with an XP install.

The older machine was a bit different as it was still running Hoary and was far too old for the online update so that got a clean install with the 32 bit disc.  Again, all very simple and quick - about an hour all told.  I have been wary on that one as it is the only XP machine in the house and has my daughters iTunes nonsense on it and I was a bit concerned about corrupting the bootloader and ruining it.  All went swimmingly though and we can now read all the XP partitions and load her iPod usung Ubuntu.

Incidentaly, I have a Tosh laptop here running Vista that is going to get Ubuntu'd once the warranty runs out or I get my act together and buy a second hard drive.  I was a bit wary of not being able to fully exploit the graphics and being unable to use the wifi facility but I ran the live CD in it a couple of weeks ago for a few days and all went fine - with the minor exception of it being unable to access my encrypted router but logged straight on to the Netgear one belonging to the guy next door. :)

---

### Post by intense.ego on 2007-12-09
So, if i understand correctly, creating a home parition and doing a fresh install is the way to go. Thanks, Incense, for the guide on creating a home partition, but does anybody have a guide on how to fresh install gutsy over feisty or is it just as easy as when i first installed it.

---

### Post by Incense on 2007-12-09
They both use the same installer. It's going to be the same experience.

---

### Post by intense.ego on 2007-12-09
Exactly what is stored on your home folder? I want to know how large to make it. I have a 48gig parition for ubuntu so what do you recommend?

---

### Post by forestpixie on 2007-12-09
I have 8GB for root, depends I suppose on what you're likely to install - I have 4Gb left, 1Gb swap and the rest for home - home gets config files afaik and anything you want to put in there -

---

### Post by intense.ego on 2007-12-09
It seems as if every file I download or create myself goes to my home folder. If I choose to save it somewhere else where do i put it?

---

### Post by Myglaren on 2007-12-09
Home does indeed get the config files plus all your personal stuff - text files, photos, presentations, music and what have you.
I have ~200Gig for the home file, 47 for root and 3Gig for the swap file that Ubuntu never seems to use.  I have a lot of photo's and music but I am still hardly using any of the drive.

---

### Post by intense.ego on 2007-12-09
in my case (48 gigs for ubuntu) what would you recommend? keep in my mind that i need enough space to download large torrents before they are moved to my external hdd. also, i keep my music solely on my ext hdd.

---

### Post by forestpixie on 2007-12-09
you'll be able to specify where your torrents get downloaded

as far as the partitioning goes I personally would do 7 for /, however much you need for swap and the remainder as /home

---

### Post by ddrplayer512 on 2007-12-09
If you have 48 gigs for Ubuntu, and you need to download torrents, well, it depends on how much software you want. I would say about anywhere from 8-15 Gigs (if you need a LOT of software) for the root partition, and leave the rest for your /home partition, however I have about 9 gigs and have 6 for the root partition and 3 for the /home partition. You may want only about 5 for your root partition, seeing as you need a lot of space for your files. In my case, I need a lot of space for my music/podcasts to sync up with my iPod.

Hope that helps!

-ddrplayer512

---

### Post by intense.ego on 2007-12-09
can you please explain to me what swap is?

---

### Post by forestpixie on 2007-12-09
same idea generally as the windows pagefile - depending on how much ram you have to how much swap to have

---

### Post by intense.ego on 2007-12-09
i have 512mb but i plan to add another gig.

---

### Post by forestpixie on 2007-12-09
I'd do a gig then - have a read of [this]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by intense.ego on 2007-12-28
Sorry for reviving this thread but I haven't created my home partition yet and I have a question: I have about 15gb (out of 48gb) of torrents that haven't yet completed. Would it be possible to temporarily transfer these to my external hdd and put them back in the home partition when I am done? Would they still download and function with KTorrent after that? Thank you in advance for your help.

---

