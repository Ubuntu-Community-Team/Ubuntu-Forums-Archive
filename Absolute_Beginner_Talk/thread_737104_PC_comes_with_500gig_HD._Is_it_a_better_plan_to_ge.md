---
title: "PC comes with 500gig HD. Is it a better plan to get two 250's?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by philinux on 2008-03-27
My local pc builder has a mid range pc that comes with a 500 gig HD. Would I be better asking for two 250's or just partition the 500.

Huge storage though. I doubt I'd use it all. Got 120gig HD now thats got about 80% free.

---

### Post by Lord Illidan on 2008-03-27
Harddisk like that calls for a massive VirtualBox collection of OSes, don't you think?

What you could do is buy 2 250GB and arrange a RAID configuration.

---

### Post by northern lights on 2008-03-27
It doesn't make a difference, go with what proves cheaper.

Unless, since you're saying you won't be using the space anyways, you'd like mirror (RAID 1) two 250 gig drives for security reasons. This would make sense if you're data were rather valuable...

---

### Post by bumanie on 2008-03-27
I'd go for the 500g and if you want a second drive, get another one. 
500g drives are the cheapest per gb at present. I have a 500g and a 320g - like you, I'll probably never use it all, but as I built a new system, I thought, why not. Have you thought of buying the parts you want and building it yourself? I got what I wanted for AUD$450 less than an already built system with the same configuration. Also knew it was built correctly and with care.

---

### Post by stefangr1 on 2008-03-27
If you use only little diskspace, if you have two similar 250GiB disks, you can mirror them (through a software array, so that a mobo change won't cause trouble). I want to make something like that myself, since any harddisk will eventually die (and they do that always on the wrong moment), but haven't come to it yet.

---

### Post by lawentzel on 2008-03-27
It is up to you what you feel most comfortable with.  I could fill a 500 gig hard drive with little trouble.  Right now I have an external 1 terabyte drive.  Partially because I like saying I have an external terabyte drive and partially because I need to backup a lot of stuff.  If you start downloading movies to your computer you tend to use up your hard drive quickly.  Personally I don't see any benefit's to partitioning your drive.  There was a time with Windows with FAT16 or FAT32 where you would want to, to get the most out of your drive.  Two drives would probably cost you more money then the one 500 gig drive.

In short, this is a personal decision.  I would use the 500 gig drive as one big drive.  But that's me.

---

### Post by LowSky on 2008-03-27
I remeber back in the early 90's when I thought having 250MB hard drive was huge and couldn't fill it. Then the Late 90's came and I could imagine filling 15GB, then I got a laptop in early 2002 with a 30GB hard drive and thought there was no way I could fill that. Now I have a desktop with 74Gig hard drive that is nearly full and a 160 gig hard drive that is getting close to full. I just purchased a 750 GB hard drive and I already have 40 GB on that. It is amazing how quickly you fill up your hard drive with games, music, video, and 2-3 OSes

---

### Post by intel on 2008-03-27
Hard disks are getting bigger & faster & cheaper,
at the same time, the amount of data lost due to disk failure is also increasing with disk size,

You should anyway be running atleast a simple
RAID 1, mirror so that 
a) your system will survive 1 DISK failure
b) your read performace will be better

merely going for 2 disk will not do,
you need to be running RAID 1 atleast

---

### Post by philinux on 2008-03-27
Thanks for all replies. Just been reading up on RAID 1. Is this set up in the bios or Ubuntu?

This is the spec for the base unit only. £270
ASUS M2A-VM MAINBOARD
ATHLON 64 DUAL CORE 5200+
2GB DDR2 800 MEMORY
500GB SATA300 HARD DISK
6X DVD±ReWriter/RAM
INT. RADEON X1250 graphics
5.1 SOUND & LAN

To have two 250gig would cost £11 extra.

---

### Post by bumanie on 2008-03-27
Pretty decent system, but I'd look at getting a nvidia gpu if I were you, they tend to work better in linux.

---

### Post by stefangr1 on 2008-03-27
You should do it trough Ubuntu, I believe this is possible using the alternate install cd. You can probably also do it trough the bios, but I would not recommend that since it limits your array to your current motherboard. If it breaks, you can't just buy another one and might have a big problem.

With an Ubuntu software array, the system should boot up perfectly if you put one or both harddisks in another pc.

---

### Post by philinux on 2008-03-27
> **bumanie said:**
> Pretty decent system, but I'd look at getting a nvidia gpu if I were you, they tend to work better in linux.

Off topic 
Their recommendation is this:-
      **512mb GeForce 8600GT** only £54

Will raid 1 affect the system performance. i naively thought 2 HD's. One with Ubuntu and separate home partition  and use grsync to backup to the other drive.

---

### Post by aaaantoine on 2008-03-27
> **philinux said:**
> Off topic 
Their recommendation is this:-
      **512mb GeForce 8600GT** only £54

Will raid 1 affect the system performance. i naively thought 2 HD's. One with Ubuntu and separate home partition  and use grsync to backup to the other drive.

If anything, RAID 1 will improve read performance.  It might *slightly* degrade write performance (due to software overhead), but that depends on CPU performance.

Running a RAID 0 myself (on a Windows box), there's definitely an improvement in read and write speed.  But with RAID 0, you have an increased chance of suffering data loss.  ...That reminds me. My desktop is due for a backup.

---

### Post by hyper_ch on 2008-03-27
HD is comming now... copying such a disc onto your harddisk will use 20-30gb.... sooner or later also games will come with much more space requirements... running them from the hd is still faster than using the drives...

---

### Post by philinux on 2008-03-27
Better get the ASUS M2A-VM HDMI motherboard then. :)

So two 250's with raid 1. Is this set up via the bios for hardware raid. Or ubuntu for software raid. Whats the package/app?

---

### Post by stefangr1 on 2008-03-27
I think you should check out this tutorial, I think everything you need to set up a raid 1 array is in it:

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

---

### Post by philinux on 2008-03-27
> **Lord Illidan said:**
> Harddisk like that calls for a massive VirtualBox collection of OSes, don't you think?

What you could do is buy 2 250GB and arrange a RAID configuration.

HaHa I'm not an OS geek but I could be tempted now.

---

### Post by philinux on 2008-03-27
> **stefangr1 said:**
> I think you should check out this tutorial, I think everything you need to set up a raid 1 array is in it:

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)


Does the live cd  not have these options?

---

### Post by stefangr1 on 2008-03-27
No, you have to use the alternate install cd for this.

---

### Post by mcdan on 2008-03-27
you could get the two 250GB drives, and use one for backup in case one fails, since you said you wouldn't use all the space anyways

---

### Post by philinux on 2008-03-27
Thanks again for replies. I'll have to make my mind up. :)

---

### Post by stchman on 2008-03-27
> **philinux said:**
> My local pc builder has a mid range pc that comes with a 500 gig HD. Would I be better asking for two 250's or just partition the 500.

Huge storage though. I doubt I'd use it all. Got 120gig HD now thats got about 80% free.

Unless you are going to run a RAID confguration get the single 500GB.  The 500GB will be faster than the 250GB as the platters are more dense.

You can always get another 500GB if you plan on running RAID.

---

### Post by stefangr1 on 2008-03-27
That is not necessarily true, since disks with higher capacity usually also have larger seek times.

---

### Post by philinux on 2008-03-27
Now I'm confused :confused:

---

### Post by bumanie on 2008-03-27
Philinux, you said you have not used more than 20% of a 120g drive, obviously you don't store huge amounts of information on your computer. Keeping that in mind, raid would probably be a waste of time and effort (although you would learn something new by trying it). Stick with the 500g drive, unless you see an obvious advantage to having raid. 
Raid is useful to some, but not others. As you know, everyone's needs and requirements are different. Some have strongly advocated raid - they probably need it. If you decide you need it later, you can always buy another drive. Don't be confused, think about what your needs are and make a decision based upon your needs.

---

### Post by IsawSp4rks on 2008-03-27
> **philinux said:**
> Off topic 
Their recommendation is this:-
      **512mb GeForce 8600GT** only £54


Get at least the 8600GTS as it performs about twice as fast the GT and is only marginally more expensive.

You can always partition the 500GB hard drive any way you want.

Pretty good system specs.  Have fun with your new PC.

---

### Post by IsawSp4rks on 2008-03-27
> **stefangr1 said:**
> That is not necessarily true, since disks with higher capacity usually also have larger seek times.

Not really much of an issue these days with SATA2, AHI (NCQ et al) and 16MB caches as standard.  Seek time variances mean so little to the average user at any rate.

---

### Post by philinux on 2008-03-27
> **bumanie said:**
> Philinux, you said you have not used more than 20% of a 120g drive, obviously you don't store huge amounts of information on your computer. Keeping that in mind, raid would probably be a waste of time and effort (although you would learn something new by trying it). Stick with the 500g drive, unless you see an obvious advantage to having raid. 
Raid is useful to some, but not others. As you know, everyone's needs and requirements are different. Some have strongly advocated raid - they probably need it. If you decide you need it later, you can always buy another drive. Don't be confused, think about what your needs are and make a decision based upon your needs.

Thanks. I was only confused by the post regarding seek times etc.

My cuurent old croc has a 17gig (ME) and 120gig ubuntu. When I installed the 120 gig I copied "My Documents" across from with windows drive. Mainly digital photo's. They consume the most space. I'm researching raid so come payday, 2 weeks time, I'll have sorted it out.

---

