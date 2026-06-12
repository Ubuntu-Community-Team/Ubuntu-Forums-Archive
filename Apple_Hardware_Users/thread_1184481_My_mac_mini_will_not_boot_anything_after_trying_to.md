---
title: "My mac mini will not boot anything after trying to install 8.10 LAMP"
date: 2009-06-11
forum: Apple Hardware Users
---

### Post by kokoroexchange on 2009-06-11
What in the world has happened here!  I've been running 7.04 (LAmP) for about 2 and a half years now on an Apple XServe G5 will wonderful success.  My logic board got fried a couple of days ago (condensation) and I got a Mac Mini to make things work until I can get the XServe fixed.

Just tried to install LAMP on my intel mac mini (2.0 GHz) 2008 model and grub wouldn't install.  I was trying to install only Ubuntu (not a dual boot) so I didn't think it was going to be a problem but now my machine won't boot anything!!!  I mean nothing!!

I've tried powering down and inserting the 9.04 desktop cd, nothing, the serer cd, nothing, rEFIt cd, nothing, my OS Leopard cd, nothing!!!  Did I just go out and buy an expensive paperweight!!!  or doorstop!!!

Sorry for my frustration but I'm desperately in need of a LAMP. 

Jason

---

### Post by kokoroexchange on 2009-06-11
Just a quick update.  I was finally able to access the disk by putting my mini in target disk mode (hold on t when powering on with a firewire cable connected to another mac that is already on) but I can't do much to the drive.  Tried to reformat it so I could hopefully install Mac OS but it won't allow me to change from MS-DOS(FAT) to a Mac OS format....

What to do??

Jason

---

### Post by kokoroexchange on 2009-06-11
I know I'm being beyond impatient but what is going on with recent versions of Ubuntu??

I've tried 9.04 in my intel Mac Mini and it seems to have rendered that machine worthless

I've downloaded and burned two PPC versions:

8.10  & 8.0.4.1

The first (8.10) wouldn't install because it couldn't find the cd drive drivers.  Strange because I installed 7.04 on the exact same laptop a couple of years ago with no problems at all.

So I tried 8.0.4.1 because I can't find 7.04 anywhere on the web and my version is stuck in my dead XServe :( and I can't get it out of the drive as there is no release mech that I can see.  I did remove the drive from the server but outside of destroying the cd drive from the XServe to get the CD out I can't see that there is a way to release it. 

Edit:  Just realized that my original subject line should read 9.04 not 8.10. 

The 8.04.1 is installing now so I just have to cross my fingers and hope that it doesn't fail at the grub install the way the 9.04 version did no my mini.  I don't want another computer that just stares at me and won't boot anything.  I don't think I could bear it.

I understand that as things evolve the 'old stuff' gets ejected out the back door but it doesn't make sense that older ppc versions would install on my laptop and newer ones won't.  Actually, no, sorry, let me clarify that.  I mean, why would an older version have no problem identifying the cd drive but a newer version be incapable of doing so...?

Pulling my hair out here trying to get something working while I wait on a new logic board for my XServe.

Jason

---

### Post by cyberdork33 on 2009-06-11
> **kokoroexchange said:**
> Just a quick update.  I was finally able to access the disk by putting my mini in target disk mode (hold on t when powering on with a firewire cable connected to another mac that is already on) but I can't do much to the drive.  Tried to reformat it so I could hopefully install Mac OS but it won't allow me to change from MS-DOS(FAT) to a Mac OS format.... What to do??

The Ubuntu partitioner likely converted the disk to an MBR format drive. In Disk Utility, select the disk to format, and choose the partition tab. Then click the Options... button and make sure it is set to GUID Partition Table (GPT). 

> **kokoroexchange said:**
>  I've downloaded and burned two PPC versions:

8.10  & 8.0.4.1

The first (8.10) wouldn't install because it couldn't find the cd drive drivers.  Strange because I installed 7.04 on the exact same laptop a couple of years ago with no problems at all. I assume you've moved on to another machine then... there was an issue with the cdrom driver on the PPC version. If you search the forum here, you will find the fix to get around it. the Jaunty PPC release seems to work much better for PPC users though.

On your Mini, did you hold the Alt/Opt key during startup?

---

### Post by kokoroexchange on 2009-06-11
Thanks, I'll try what you've suggested here later today.

Also, yes I did try holding alt/option when trying to start up but it had no effect.

Jason

---

### Post by kokoroexchange on 2009-06-13
Anyone who can help,

I managed to regain control of my mac mini but I am not sure how.  I left it for a day and installed my Ubuntu LAMP on an old PPC laptop just to get our website up.

Came back to my mac mini and restarted and the rEFIt CD that was stuck in the machine booted!  Wow!  The problem is I had already reformatted the entire drive with FAT32 MBR so there was nothing for rEFIt to do.  I was able to get the CD out and when I put the 9.04 server disk in the machine it booted!!  Wow again!

So, I thought I'd try the install again as explained [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation").  But, I still run into the same problem.  It cannot install Grub.  

I'm stuck.  Haven't tried to return the mini to some working state by installing OSX on it yet because I wanted to use it as a server but maybe I'll give that a shot for now and try using rEFIt...

Any advice will be appreciated.

Jason

---

### Post by cyberdork33 on 2009-06-15
> **kokoroexchange said:**
>  So, I thought I'd try the install again as explained [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation").  But, I still run into the same problem.  It cannot install Grub.  

I'm stuck.  Haven't tried to return the mini to some working state by installing OSX on it yet because I wanted to use it as a server but maybe I'll give that a shot for now and try using rEFIt...

Any advice will be appreciated.

JasonIt is odd that GRUB is not installing, but reformatting to a GPT-style disk may be all that you need. You do not have to install OSX on the machine... Though, installing to an external drive may be a good option in order to have a backup bootable drive in the future... plus this will allow you to perform firmware updates if the need arises.

If you reformat to a GPT disk, then you do not have to install rEFIt, you can 'bless' (with OSX) the linux boot partition (or root partition if they are not separated... though they should be on a server imo). You can still have rEFIt on the EFI partition if you wanted, but you would still need to bless rEFIt before it would boot. See the posted FAQ for info on blessing.

Also, have you thought about using OS X? you can run a LAMP stack -L +O. Though the setup is a bit odd on OS X.

---

