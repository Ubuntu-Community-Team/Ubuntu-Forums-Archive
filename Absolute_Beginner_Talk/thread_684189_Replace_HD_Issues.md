---
title: "Replace HD Issues"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by theRevMom on 2008-01-31
Okay, I'm back to square one.  

I have a failing HD.  I bought a new one and have physically installed it. When I tried to run the set up cd, it would not run because I don't have the correct drivers for the video card.  Won't run in the safe video mode either.  

So, I've put the failing drive in as the master, the new one as a slave.  I now can boot to the old HD which has Edgy on it.  But I can't figure out how to find the new HD so I can 
1. Format it,
2. Install Gutsy on it
3. Copy my data from the old to the new.

This HD will run for a while then  over load and shut down.... so I'm on a limited time and I don't know how to find this thread again short of book marking it...

Help!  I've lost my brain and I don't know........  :)

---

### Post by brettg on 2008-01-31
What do you mean it won't run? The LiveCD won't load perhaps? 

You could try d'loading the alternate CD and do a text mode install.

Alternatively, if you do want to set the new drive up as a slave then be aware that once you install Gutsy on it and remove the failing hdd you will need to manually build the MBR on the new drive as it will not yet have one.

Good luck.

---

### Post by bumanie on 2008-01-31
I would suggest you should check your bios settings to ensure the new hard drive is being recognised correctly. Whilst in bios you should ensure that it is set to boot from cd-rom, if it's not you won't be able to start a live cd. Also I would get gparted a live cd and see if you can format your new drive with that. It's a live cd partitioning program.

---

### Post by Moop on 2008-01-31
Everytime you use the old drive you run the risk of losing everything on it. Unplug the old hard drive and install gutsy from a live cd to the new hard drive. 

After that's done you can plug your old hard drive back in and deal with getting your data transfered. 

Ifv you don't have a live cd and your pc won't work long enough to download and burn one, maybe a friend can burn one for you. :guitar:

---

### Post by bumanie on 2008-01-31
To retrieve files etc. you shouldn't need to install ubuntu, you should be able to do that from the live cd. If your new drive is an ide, double check your jumper settings. Until you get your new drive working, if you have an external hard drive or large capacity usb pendrive,  you could transfer files to one of those devices.

---

### Post by theRevMom on 2008-02-01
Thank you everyone for your help.  The old HD isn't completely dead yet, but I discovered that it's the original HD from this machine:  purchased in April 2oo1!  It's a 40 Gig Seagate that came with this E-machine T1742 (1.7 Ghz Celeron with 1 gig RAM).

Here's what I've done.

I downloaded GParted and used it to partition and format the new hard drive.... initially it would not recognize the video drivers either.  It would not work using the Force Vessa Script.  Through trial and error I found one that would work from the Gparted CD.  

That accomplished, I installed Gutsy fresh on the new HD, used FoxMarks to sync my bookmarks, copied my Thunderbird address book from the old HD (set up as a slave) and copied all the docs from the old HD.  

The only thing I can't get to copy over are the MP3 files.  It requires too much read-time on the old HD unless I do it one file at a time and stop in between. Since I have over 300 files, I'm writing a script to do this over a 24 hour period.  At least with the new HD it's not going to shut down in process when the HD stops.  And if I don't get everything off of it, well, I do.  That's the price I pay for not backing it up more frequently.  

Again, thanks for the help!  I LOVE this community!

---

