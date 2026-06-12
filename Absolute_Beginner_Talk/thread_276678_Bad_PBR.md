---
title: "Bad PBR"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-10-13
Hello everyone,

I feel a bit bad about this because I gave my brother-in-law a Dapper CD to try. He tried it at work and it worked fine. And co-workers got to take a look at it which is good news! So far so good!

He went home and tried there on his brand-new Dell desktop computer. Now all he's got is "bad pbr" on the screen and can't even boot Windows.

I googled but found very little on the subject; even a bug report was left unanswered.

Anyone has a clue?
Thanks for reading.

---

### Post by Rhubarb on 2006-10-13
It's funny you say that, as for the last 2 weeks I've had a work mate's dead dell sitting under my desk that had suffered the "bad pbr" problem.  I haven't installed Ubuntu on it, as he'd paid for windows and only wants windows.
It generated the bad pbr problem "by itself", I'm guessing it had file sharing programs and heaps of malware.
I had a look at the drive from the dapper live cd using GParted.
Looks like his entire xp partition is dead, along with any remnants of what was a restore partition.
(He didn't get a windows cd with the computer, so he's up s**t creek without a paddle).
One interesting thing I found, was that the bad pbr error that comes up on screen seems to come from what's on the hard drive, irrespective of which computer you plug it into.  So it seems that either something is wrong with the mbr (master boot record), or there's something wrong with the dell software on the hard drive.
Anyway, if you look at the attached screenshot here you'll notice that there are a few partitions, the extended partitions were created later with partition magic.
There's a 70MB FAT 16 partition at the very start of the drive, I think this is the part that's giving you this bad pbr error.

If you want to install ubuntu (Duh, of course you do), be sure to run GParted before running the installer.  Delete all the partitions you see, then run the Ubuntu installer.

---

### Post by dmizer on 2006-10-13
pbr is partition boot record.  something happened to it.

you can have him try to disable the cdrom drive as a bootable device.  that should get him back into windows.  this can also happen when there are multiple drives installed in the machine too.

if not, he should be able to boot to the windows install cd ... then try performing a master boot record fix.

---

### Post by Rhubarb on 2006-10-13
Yeah a fixmbr might work, I didn't try it personally as I didn't want to void my workmate's Dell warranty (I don't know what the Dell warranty is).

I did try a fixboot but that didn't work either.

I'm of the consensus that the MBR is fine, it's just the partition that windows is on is scrambled (not the 70MB FAT16 partition that I'm guessing is still there on xyz's stepbrother's pc).

I personally don't like dell too much, and certainly not with windows.

---

### Post by xyz on 2006-10-13
Thanks a lot for the support guys! I've gotten in touch with my in-law and he's checking it out!
I also found this
[http://blog.eop.org.uk/121-ubuntu-606-update-help/](http://blog.eop.org.uk/121-ubuntu-606-update-help/)
if anyone cares to have a look!

---

### Post by Rhubarb on 2006-10-13
Please post your findings here xyz.
As my workmate today would currently be running through the dell diagnostics that dell "support" have advised him to do.
I think this diagnostics thing that Dell has asked him to do is a total waste of time, the drive is foobared.
I think the whole lot needs to be wiped and start from a clean install (of Ubuntu, or windows if you really want to).

I can't stress how important it is to have a recent backup of all your programs and data, and to have your Ubuntu / windows CDs at hand.

As for Dell and their buddies at m$ ... well I can't really say as these are public forums, and as such children maybe reading this.

---

### Post by Rhubarb on 2006-10-17
Well, looks like Dell are sending out a recovery DVD out to him.  Should take a week to get to him they say.

... Meanwhile the old Dell laptop that I installed Ubuntu on for him is still chugging away quite nicely - even after he accidentially deleted all the files (including all the hidden ones) in his home folder.

---

### Post by Iowan on 2006-10-17
So I take it Bad PBR isn't a comment on the flavor of Pabst Blue Ribbon???:-k 
(sorry... I'm outta here).

---

### Post by xyz on 2006-10-18
Well, my in-law -the one who's having this pbm- is away on vacation. He left his box 'as is' and will get back to it when he returns.
So more about this when he gets back.
Thanks for your time so far, though!

---

### Post by xyz on 2006-11-20
Hey Rhubarb...funny you PM me today!! I finally had advised my in-law to try to contact Dell and ask them to send him CDs to fix his problem which they did! He got them in the mail this morning and just reinstalled. Yes it works now but I wish I could understand what he did to mess ip all up that way.

His total lack of knowledge about Linux makes any explanation impossible. Needless to say he's not longer that 'hot' on Linux; he can't admit he did something wrong!! So it's all Linux's fault!!Not a big loss for the community, I guess!!

Seems stange to me that Dell delivers pre-installed Win Multimedia computers and do not include some kind of CD to fix things in case of problems...I mean (lol) like Windows will never encounter the slightest problem...

Thanks for your PM! Good day.

---

### Post by Rhubarb on 2006-11-20
My work mate's Dell with the PBR problem is now working again.
The win xp cd that Dell sent out to him fixed the problem.
He did however have to go onto Dell's website to download some drivers ... which included his network card's driver!
So I got him to download all the relevant drivers for his Dell on his old laptop (running Ubuntu) onto a flash drive.

... All up his Dell was offline for about 4 weeks.  And even required Ubuntu to get it working again.

I had asked him why use windows at all if it'll take your computer down for a month?
The answer: Because his family doesn't like change (or the idea of change), and that they'd paid for windows with their Dell, so they'd better use it.
... Which doesn't make a whole lot of sense.  If you bought a hair dryer that gave you an electric shock every time you used it, would you keep on using it "because you paid for it" when there are other hair dryers that are free and work properly?
](*,)

PS, the reason why he's got a laptop with Ubuntu on it, was because he bought it on ebay and it didn't come with the windows CDs.  Windows did not want to install on it (no CDROM drive, no FDD), so I took great pleasure in installing Ubuntu!

---

### Post by xyz on 2006-11-20
> Windows did not want to install on it (no CDROM drive, no FDD), so I took great pleasure in installing Ubuntu!
;)  :D
> "because you paid for it" when there are other hair dryers that are free and work properly?
My thought exactly! People feel 'cheated' if they don't use what they bought even if it brings them one pbm after another! Masochism, I wonder? Stinginess?

His Dell (Desktop) being very new, no need to go search for drivers or anything else!
Maybe he'll grow up some day and we'll be able to talk Linux again? Because in his mind, it's Linux's fault BUT it's really MINE because I put that 'evil Ubuntu CD' in his hands!!So folks don't follow any advice even when they don't know the 1st thing about anything.
Oh well...time heals all wounds, they say!

---

### Post by Rhubarb on 2006-11-20
> **xyz said:**
> His Dell (Desktop) being very new, no need to go search for drivers or anything else!

Well, the Dell here in question was only bought in February this year (2006).  So it's new enough.
I think Dell must've sent him out a generic win xp CD, not one with the correct drivers specifically for that model.

Another thing, he did somehow manage to delete the entire contents of his home folder (not from any nasty software, just by user incompetence), but all it did was set some things to their defaults.  He managed to set it all back up so everything is now running smoothly.

---

### Post by xyz on 2006-11-20
> Well, the Dell here in question was only bought in February this year (2006). So it's new enough.
I think Dell must've sent him out a generic win xp CD, not one with the correct drivers specifically for that model.
Yess indeed it's quite NEW!!

I only had the man on the phone but he told me he got 3 CD's from Dell.
I guess I'll be dropping by his house one of these days and find out more about it.

---

### Post by smoker on 2006-11-20
makes me wonder why companies like dell dont supply cd's, surely it cant be to save money!

reading this i'm taking dell off the possibilities for my next system,

---

### Post by Rhubarb on 2006-11-20
> **smoker said:**
> makes me wonder why companies like dell dont supply cd's, surely it cant be to save money!

reading this i'm taking dell off the possibilities for my next system,
Well, as far as I can tell it is exactly so Dell can save some money.
Quite a lot of big computer manufacturers have a recovery partition on the hard drive (which is absolutely useless to have IMO).
When buying a new PC from Dell's website you have the option of paying for a recovery CD - costs &#8364;5.00
I know HP have done it a different way, they also have the recovery partition on the Hard drive, but once in windows it offers to burn recovery CDs / DVDs for you ... they just don't supply you with any blank media to do so.

If you're a bit of a techie, why not buy the computer parts and build yourself a custom PC?  Depending where you buy the parts it's often much cheaper than any brand name manufacturer.

---

### Post by Anemos on 2007-05-11
Hello, this is my first post here. I'm fairly new to ubuntu, thoug not to linux in general. i tried to install ubuntu off  an self burned cd-r, used "use free space on disk" beliveing it would not affect my windows partition. i rebooted, got the message "bad PBR". as a student this was the equivalent of death- death plus a supposedly lost computer. i had ordered the cd several weeks before, abnd recived it today. i could not boot into the self-made livecd. before tossing in the virtual towel, i tried to boot to my new cd for the hell of it- success! i then went into gParted, and set the windows partition flag to "boot" (Not the FAT partition, thats the MBR(i belive everyone knows this but there was no advice anywhere on my situation, one that is definitly deserving of advice. i then rebooted, and YES! windows began to load, allowing me to post this. I assume my problem was not installing GRUB first. I love ubuntu, despite the total hell i went through for a month unable to get my schoolwork done.

I belive there needs to be better documentation for installation as I am still unable to set up a simple dual boot with windows. :(  I hope this helps someone out there- Milo NC 


(side note: if anyone would mind telling me how to do it properly in their own words, please let me know.)

---

### Post by xyz on 2007-05-13
Hi there,

Glad to see it all worked out for you in the end.
Here are a couple of good links to dual booting:
[Hermann's]("http://users.bigpond.net.au/hermanzone/p3.htm")
[Psychocats]("http://www.psychocats.net/ubuntu/partitioning")
Hope it helps. Good day.

---

### Post by Anemos on 2007-05-28
Thank you, I'm suprrised that this (according to google anyway) this is the only page about this issue...although i'm glad to say the issue is fixed, i was posting so others who find this can fix their problem with relativly little pain.

---

### Post by PRMan on 2007-06-05
I dug into this a little and got everything working without wiping the drives (but I have to boot from a USB flash drive now):

[http://ubuntuforums.org/showthread.php?t=459180](http://ubuntuforums.org/showthread.php?t=459180)

---

### Post by squeakyfrommage on 2007-10-17
WARNING! This solution will probably only work for an install on a new machine (unless you don't care about losing data)

The dell utility partition is about 47 MG and is installed at the very beginning of the cylinder.  After trying to install Ubuntu Server on a machine that was purchased without an OS, I kept getting the PBR error because the installation had removed that partition. I eventually got my system to work by redoing my paritions and creating an empty, non-mounted partition of the same size, creating it as the first partition. My boot partition then went on as second, and I now have no problem booting.  

I'm not sure how well this would work for dual-booting, but I didn't find this solution anywhere else, so I thought I'd add it to the information available.

---

### Post by iHateMyComputer on 2008-01-30
Can anyone tell me where I can get the CD that fixes this?

---

### Post by xyz on 2008-02-01
> **iHateMyComputer said:**
> Can anyone tell me where I can get the CD that fixes this?

HI,
What CD are you talking about?

---

### Post by iHateMyComputer on 2008-02-02
The CD that Rhubarb said worked for him. I assumed it would be available on the Dell website but when I searched the bad pbr all I got was some links to their community forum with no info on a CD. I tried PMing Rhubarb before posting in here but I haven't gotten a reply so I was hoping someone else knew where I could get it.

---

### Post by Rhubarb on 2008-02-05
Sorry for not getting back earlier to you.
You can get the Dell recovery CD by calling up Dell technical support.
Tell them that it comes up with "Bad PBR" on start up, and follow what ever they say (which is mostly useless 'problem solving' that lasts for an hour on the phone).

They should tell you that they're sending out a recovery DVD in the mail to you, if they want to send out a technician, tell them that you just need the recovery DVD to fix up the issue - as you've read similar problems on the Ubuntu forums that have been fixed up nicely.

---

### Post by iHateMyComputer on 2008-02-06
Ok thanks for the help man

---

### Post by xyz on 2008-02-08
I don't know where you live but here they "repair" over the phone. They have a sort of "hidden partition" they don't want you to know about.

I "converted" a friend of mine to Linux because he got soooo tired of the time it took to try and fix it that way and at the end of the day....it didn't fix it at all.

Good luck.

---

### Post by sohryu on 2008-06-10
i think its related to a windows update.. issue happens on both XP and vista... reimage the HDD solves this and turn off the auto updates to prevent it from comin back.

---

