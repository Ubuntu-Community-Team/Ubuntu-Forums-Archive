---
title: "Xubuntu CD check fails on one machine, works on another"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by skylar.sutton on 2008-03-26
I'm attempting my first Xubuntu install on an old Dell Lattitude (CPi series). I verified the MD5 checksum on the ISO before burning, burnt at 1x (wow I forgot how long that takes!), and ran a CD check before starting the installation. About 25% of the way into the CD check it begins to fail. ISO file is: xubuntu-7.10-alternate-i386.iso

After two or three re-burns I started to think it's not the CD's fault so I popped it into my desktop, booted it up and ran a CD check there. On that machine the CD passes all checks and gets the Xubuntu stamp of approval. 

I think the drive is fine as I used it to install a copy of Windows 2000 a few weeks back with no errors. 

Anyone have any thoughts? Thanks,

 - Skylar

---

### Post by hyper_ch on 2008-03-26
> **skylar.sutton said:**
> Anyone have any thoughts?

Not really.. this seems really to be strange... do all discs fail at the same point of the cd checking?

---

### Post by learntoswim on 2008-03-26
im having the same problem but im trying ubuntu not xubuntu =\

---

### Post by toupeiro on 2008-03-26
It still could be a dirty lens on the CD-ROM

Or, a problem with the CPi.  I used to work at a place years back that used CPi-A latitudes and I can attest that the earlier ones had problems with CD-R80 media (CD-R80 is extended format media.  CD-R74 was the original stuff)

Advice:  Check DELL's website and download the latest available BIOS update for the CPi-* model you have.  Make sure to follow directions closely on how to properly flash your BIOS if you've never done so before.  Dell will provide these directions for you free of charge, and they are accompanied with the BIOS Download most of the time.  There is a good chance the problem has been addressed IF its having a problem with the CDR format.

---

### Post by skylar.sutton on 2008-03-26
> **hyper_ch said:**
> Not really.. this seems really to be strange... do all discs fail at the same point of the cd checking?

It's not always the same file that fails, but it is the same cluster of files that fail. (i.e If the file order is A, B, C, D, E, F, G... it will be files C, D, or E that fail every time).

---

### Post by skylar.sutton on 2008-03-26
> **toupeiro said:**
> It still could be a dirty lens on the CD-ROM

Or, a problem with the CPi.  I used to work at a place years back that used CPi-A latitudes and I can attest that the earlier ones had problems with CD-R80 media (CD-R80 is extended format media.  CD-R74 was the original stuff)

Advice:  Check DELL's website and download the latest available BIOS update for the CPi-* model you have.  Make sure to follow directions closely on how to properly flash your BIOS if you've never done so before.  Dell will provide these directions for you.

I flashed the BIOS to A12 before I started (that was the latest version)... I haven't tried an R74 CD yet. I assume the R80's are the 700MB discs and the R74's are the 650MB disks?

---

### Post by toupeiro on 2008-03-26
> **skylar.sutton said:**
> I flashed the BIOS to A12 before I started (that was the latest version)... I haven't tried an R74 CD yet. I assume the R80's are the 700MB discs and the R74's are the 650MB disks?

That is correct :)

---

### Post by toupeiro on 2008-03-26
> **toupeiro said:**
> That is correct :)

One more piece of advice to try if the format change didn't work:  Burn your ISO with a different application than you've been using.  Not all programs close their CD session the same way, and older CD-Roms were very picky about this sort of thing.

IN linux, you can try k3b or from the command line, cdrecord, if you were using gnomes default (serpentine, I think) 

In windows, if you were using something like NERO, download something called burnatonce, which is a very good, free, ISO burner.

---

### Post by skylar.sutton on 2008-03-26
> **toupeiro said:**
> That is correct :)

I was going to say I will try that when I get home... but I just realized the alternate ISO is over 650MB. Is there anything I can trim out of it to fit it on the smaller media?

---

### Post by toupeiro on 2008-03-26
If you aren't doing one of the following:

# creating pre-configured OEM systems;
# setting up automated deployments;
# upgrading from older installations without network access;
# LVM and/or RAID partitioning; 
# nstalls on systems with less than about 128MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).

then you shouldn't need the alternate ISO, and should be fine with the standard 32-bit desktop download which is like 566MB.  

I will say that I used a standard desktop ISO when i installed on my Toshiba Libretto with 128MB ram and it went successfully (slow, but successfully)

In any regard, it is still worth trying a different burning tool.

---

### Post by maljaros on 2008-03-26
I have no wisdom to offer, just a description of a related experience.  The DVD from latest edition of Linux Format magazine had iso images of FreeBSD.  First burn attempt at 4x produced corrupt discs, as did 2nd attempt at 1x.  The third attempt done at "fastest possible" speed (don't ask - I just thought it was worth trying) produced a successful disc.  All of this (burn/read) was in the one Combi drive.  Maybe the newer drives don't like to burn at slow speeds?

---

### Post by c-ron on 2008-03-26
Almost every brand of 650 MB CD-R can go burn over 665 MB of data using over-burning.

---

### Post by toupeiro on 2008-03-26
maljaros has another very valid point.  Burn speed did have an effect on earlier generation CD-ROM's.  you can try dropping your burn speed, and it may do the trick as well. 

I guess you have a few things to try. :)  Let us know how things go.  Good luck!

---

### Post by skylar.sutton on 2008-03-26
Here's an update...

[LIST]
[*]As indicated in the initial post, discs have always been burnt at 1x. That always seems to be everyone's first piece of advice in the forums so I figured I would take that out of the equation from the beginning. 
[*]I used burnatonce to burn an alternate install ISO AND the standard install ISO. Details below...
[*]I felt like having a laugh so I tried to install the alternate disc even though the disc check failed. As you would expect the install failed (it made it all the way to the final phase where it's physically copying files... then it died with a "file not found" exception).
[*]The standard install disc fails the cd check with a generic "I/O Error". 
[*]I have NOT tried using a 650MB cd... because I can't find any! Gave up after the third store, no luck when I raided my PC cabinet at home. 
[/LIST]

Unless anyone has any new suggestions I think I'm going to have to give up... which is real disappointing.

---

### Post by rkd on 2008-03-26
I don't hold much hope that this will work, but let me mention it, in case you want to try it.

As far as I can see, you haven't said whether you have been using the same CD drive to write all of your discs for the install attempts.  If you have written all of those discs on the same drive, there is a small chance that writing one on a different drive will make a difference.  I think it is a very small chance, but if you have nothing else to try, it might be worth a shot.

From your description, it sure seems like there is something wrong with the CD drive on the Lattitude, since the discs check out okay on other systems, but fail the check on the Lattitude.

Another sort of off-the-wall thing to try is to try to install 7.04 rather than 7.10.  I don't have any clear reason why that might work, but when nothing else works, you might as well try oddball things.

I'll bet there is a way to install with the Xubuntu files located on another machine, accessed over the LAN, like some places do when they are doing unattended installs from a server, but I don't know how to do it, and it probably isn't something you would be able to get working on your own.  

If you can locate a Linux User's Group near you, you might be able to find someone there who could help you.  If you want to do that, but don't know how, ask about it here and we can help you find one.

---

### Post by skylar.sutton on 2008-03-26
I have been using the same drive to burn all of the cd's... I'll try my wife's PC as the burner tonight and see if that gets me anywhere. 

I'm pulling down a copy of Xubuntu 6.06... maybe I'll get lucky. If it works I should be able to force an update, correct?

---

### Post by rkd on 2008-03-26
Well, it is possible, at least in theory, to upgrade from one version to another, but I've seen a few posts describing problems, sometimes pretty severe, that occur when doing such upgrades.  Often, the problems were solved by doing a clean install of the later version.

So if you get 6.06 installed, you can try the upgrade path, and it might work fine for you, especially if you upgrade right away, without trying to customize the system first.  But if that doesn't work, it might be best to reinstall 6.06 from scratch and stick with it.  It is the long-term support version, so you'll get updates for another year or two (I don't remember what the promise is, exactly).  After that, if you haven't replaced the Lattitude by then, you might have to replace it at that point in order to move to a later release.  Or spend more time figuring out what the problem with the CD drive is.

Hmmm. Can that Lattitude boot from an external USB CD drive?  If so, that would be another thing to try, if you have or can borrow, such a drive.

---

### Post by shadowbw on 2008-03-26
You should definitely give the alternate install cd a try.  I've installed Ubuntu on a couple of computers that would absolutely not load the regular install disc.  You might also try over the network install......or perhaps a USB install, either of those you'll have to google steps on how to do.

shadowbw

---

### Post by Logistics64 on 2008-03-26
....My Xubuntu CD does that too, really makes me angry...

---

### Post by IsawSp4rks on 2008-03-26
Why not move the install to a USB flash drive and install xubuntu from there?  Of course you'll need another PC with Ubuntu on it to move the install from .iso to the USB Flash drive.  Also, replace the .iso in the docs listed with your xubunutu iso file.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most Dells can boot from a USB flash drive, so that should avoid any issues you have with your combi drive.

Good luck.

---

### Post by skylar.sutton on 2008-03-26
Thanks for the suggestions all. 

I gave up on Xubuntu/Ubuntu and went with a copy of Fluxbuntu. That CD loaded right up and passed all the CD checks. *shrug*

Install's at 99% so I'd say it's safe to assume it's working.

---

