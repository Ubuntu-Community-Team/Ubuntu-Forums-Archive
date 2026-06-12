---
title: "Dual Boot (Ubuntu Fiesty First)"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-08-29
Here's my setup:

1.6 ghz Core 2 Duo
1gb ram
256mb nvidia geforce go7400
100gb HD

So taking the advice of my friend I installed Ubuntu 7.04 on my laptop. Completely erasing my windows partition. 

Now I really want to use windows (specifically to play games). So I partitioned my HD, using gparted I resized my ext3 partition and made an ntfs partition (split about 60gb - 35gb).

I put in my windows cd and upon starting up I got the following message (paraphrased):

Setup cannot detect a hard disk, setup is exiting

So I just deleted the ntfs partition (left it as unallocated) and tried it again, with the same message.

Any thoughts?

---

### Post by fjf314 on 2007-08-29
I may be completely off the mark with this, but what kind of hard drive do you have? If it's a SATA drive, you will need to load the drivers for it seperately before your XP disk will be able to recognize it. When your machine first boots from the CD, you will see an option at the bottom of the screen to press one of the F keys (I can't remember which one, it's been awhile) to load any additional drivers. At that point you'll need to have the SATA drivers on a floppy so you can load them.

Also, in this instance you might be better off just trying to back up your /home directory in Ubuntu, starting over, and installing Windows first. While I haven't dual-booted in some time, I've always heard that the Windows boot loader doesn't play nicely with other operating systems, so it's almost always best to have Windows installed first before dual-booting with any other OS.

---

### Post by boogieboarder97 on 2007-08-29
i have my laptop dual booting xp and ubuntu fiesty and it works perfectly. i would also suggest installing xp first then run a disk check and defragment the harddrive through xp. then put ubuntu in and launch the installer. when you see the screen that asks how you want to partiotion the drive you should click the one that will do it automatically but do not click use entire harddisk. then youll see aslider bar and give it however many gigs you need.

---

### Post by abhiroopb on 2007-08-29
OK so basically here is the problem.

From what I've been reading I understand that HP's have SATA drives which is not recognised by Windows XP.

Incidentally I have been trying to install a Modified version of XP. Although both the normal and modified versions don't recognise the drive. Usually HP comes with its own reformatting partition, but with the installation of ubuntu I deleted that. In any case as it stands I need to install SATA drivers somehow (as fjf said). Since I have a laptop floppies are too much trouble.

I have heard of nliteos though and I was wondering if someone could shed some light on this. So basically this is my issue:

I have an iso of the modified OS onto that I would like to add the SATA drivers and then just install it anyway I can (I have an image of the ubuntu installation so it isn't much trouble to delete it and start over). Also I have two other programs (nvidia graphics driver and Game XP) which I would like to integrate onto the nliteOS. Essentially I want to use it SOLELY for games, not net nothing (saves having an anti-virus). 

So could someone please explain the procedure. I can figure out how nliteos works but its the SATA drivers that I'm more worried about integrating.

---

### Post by abhiroopb on 2007-08-29
I think the HP drive I have is ATA-5, is that the same as SATA?

---

### Post by wetland on 2007-08-29
This [link]("http://www.computerhope.com/help/ide.htm") will tell you about your ATA-5.

As boogieboarder97 stated xp first would make things much easier.

---

### Post by abhiroopb on 2007-08-29
Like I said I tried that. I reformatted everything. Basically I tried the entire HD as ntfs, and then as unallocated. I loaded up the windows cd and it still couldn't detect. So, I am assuming that it is a SATA issue. Could someone please provide some insight on how I can install the drivers without a floppy? Such as using nliteos. As far as I can see there are many people on this forum with this problem. Unfortunately I can't find a suitable solution.

---

### Post by dorath on 2007-08-29
abhiroopb, 

There are two options for drivers that XP doesn't have by default:

1.)  F6.  During text-mode setup you're asked to press F6 if you have any drivers you'd like to use.  This, IIRC, requires the use of a floppy drive.  If you can obtain drivers for your SATA controller on a floppy, and if your laptop has a floppy drive, then this option is the easiest.

2.)  'Slipstreaming', and it's a handy skill to have if you work with Windows.  In the past I've used [nLite]("http://www.nliteos.com/index.html") many times to do this, and have been fairly happy with it.

To get started you'll need an XP CD, and you'll need the proper XP SATA drivers which you should be able to download from whoever made your laptop (Dell, HP, whoever).

Instructions on exactly what to do are best read on the nLite site, but in short you're going to make a brand new XP CD that includes the drivers you need.  While you're at it, you can actually include nifty things like service packs, the latest video drivers, etc, but those are totally not necessary.

EDIT:  You'll know if your SATA driver slipstream works if your drives are detected.  If they're not, something is wrong.

---

### Post by wetland on 2007-08-29
I would suggest looking up how to load your OS to a replacement hard drive on the HP site. I know you didn't install a new drive but you did wipe it clean just like a new one. Also you might need to reformat it just a shot here but maybe windows is not seeing the hard drive because it is formated to a linux file system. How do I do that? use a live cd. mount it and use gparted.

---

### Post by abhiroopb on 2007-08-29
> **wetland said:**
> I would suggest looking up how to load your OS to a replacement hard drive on the HP site. I know you didn't install a new drive but you did wipe it clean just like a new one. Also you might need to reformat it just a shot here but maybe windows is not seeing the hard drive because it is formated to a linux file system. How do I do that? use a live cd. mount it and use gparted.

OK thanks for your input guys.

So basically I used a system rescue cd and gparted a while back to try out the different formats. Such as fat32, ntfs and leaving it unallocated. None of it worked unfortunately. 

I suspect the best thing to do is go the slip-streaming route. I sent of an e-mail to HP I'll see what they have to say. Untill then I am looking on their website for the drivers.

---

### Post by abhiroopb on 2007-08-29
> **dorath said:**
> abhiroopb, 

There are two options for drivers that XP doesn't have by default:

1.)  F6.  During text-mode setup you're asked to press F6 if you have any drivers you'd like to use.  This, IIRC, requires the use of a floppy drive.  If you can obtain drivers for your SATA controller on a floppy, and if your laptop has a floppy drive, then this option is the easiest.

2.)  'Slipstreaming', and it's a handy skill to have if you work with Windows.  In the past I've used [nLite]("http://www.nliteos.com/index.html") many times to do this, and have been fairly happy with it.

To get started you'll need an XP CD, and you'll need the proper XP SATA drivers which you should be able to download from whoever made your laptop (Dell, HP, whoever).

Instructions on exactly what to do are best read on the nLite site, but in short you're going to make a brand new XP CD that includes the drivers you need.  While you're at it, you can actually include nifty things like service packs, the latest video drivers, etc, but those are totally not necessary.

EDIT:  You'll know if your SATA driver slipstream works if your drives are detected.  If they're not, something is wrong.

Finally found the required driver from the HP website. Now I just need to sort out nLitel. How does it work exactly? Can I do it from ubuntu? Can I add some install files to it?

I'm looking at their help files but any other input would be appreciated.

---

### Post by abhiroopb on 2007-08-29
Last thing. Well a few of things really. 

1. Will nLite support the modified version of XP. I'm assuming it would because all nLite requires is that I copy all the files on the CD onto the HD.

2. I want to integrate my nvidia driver. But I think its an .exe file, and from what I read nLite only takes driver files which are .inf how shall I solve this?

3. Same problem with my SATA driver

4. By loading the SATA driver where nLite tells you to load drivers will it work? What I mean is when the setup is starting will the installation detect the SATA driver?

5. I have a program (called GameXP) that apparently tweaks your XP settings to make it easy to play games

---

### Post by wetland on 2007-08-29
> **abhiroopb said:**
> 
 So I partitioned my HD, using gparted I resized my ext3 partition and made an ntfs partition (split about 60gb - 35gb)

Now I see missed that. I would still suggest wiping it clean to all ntfs using a live cd. Install dowz first using the 35gb partition leaving the other 60gb unallocated for the ubuntu install.

What model laptop we talking about?

---

### Post by abhiroopb on 2007-08-29
My laptop is HP dv5242ea. Actually I tried everything with my HD. formatted everything and tried with ntfs, fat32, and unallocatted. I think the problem was with my SATA drive. So, I've found the driver from the HP website. When I get home I'm going to try using nLite to slip-stream the driver. Hopefully that will work. I had a few q's if someone could answer them...

---

### Post by abhiroopb on 2007-08-29
1. Will nLite support the modified version of XP I downloaded? I'm assuming it would because all nLite requires is that I copy all the files on the CD onto the HD.

2. By loading the SATA driver where nLite tells you to load drivers will it work? What I mean is when the setup is starting will the installation detect the SATA driver?

3. I have a program (called GameXP) that apparently tweaks your XP settings to make it easy to play games can I integrate this into it as well?

4. I'm planning on running a purely gaming version of XP, so I don't even intend to have internet. So ideally I don't want to have to download any of the service packs or hotfixes, would you say that these are recommended?

---

### Post by dorath on 2007-08-30
> **abhiroopb said:**
> 1. Will nLite support the modified version of XP I downloaded? I'm assuming it would because all nLite requires is that I copy all the files on the CD onto the HD.Try it.  I've never tried with a cracked version, and I never would.

> **abhiroopb said:**
> 2. By loading the SATA driver where nLite tells you to load drivers will it work? What I mean is when the setup is starting will the installation detect the SATA driver?If you follow the directions, it will work.  I used nLite to slipstream the SATA drivers for my XP and XP64 installations.

> **abhiroopb said:**
> 3. I have a program (called GameXP) that apparently tweaks your XP settings to make it easy to play games can I integrate this into it as well?Maybe.

> **abhiroopb said:**
> 4. I'm planning on running a purely gaming version of XP, so I don't even intend to have internet. So ideally I don't want to have to download any of the service packs or hotfixes, would you say that these are recommended?If you're going to unplug your box from teh internets before booting to XP, you'll be fine.  If you ever access the internet, even by accident, you'll want Service Pack 2 at a bare minimum.

---

### Post by abhiroopb on 2007-08-30
Thanks for you're replies. I contacted HP actually and apparently you can just disable SATA native support and install XP. I intend to try that out. As you said I should have SP2 if I access the net, well I don't intend to at all, but what about any requirements for games? The newest game I have is F.E.A.R. Extraction Point do you think it requires an add-ons from MS? Such as .Net Framework?

---

