---
title: "ubuntu mac cd bootable?"
date: 2006-08-03
forum: Apple PPC Users
---

### Post by electroconvulsive on 2006-08-03
I have downloaded and burnt an image of dapper for ppc that is going on an old 333mhz imac. This imac has no operating system on it at all currently as I found it on a local council clean up :p and I had to replace the hard drive whaich had obviously died on the last owner and he or she was probably afraid to open it up. Anyway the image was burnt to a cd. And the mac will not recognise the disk at all let alone boot from it. I have tried to stick other cds into the drive to see if the machine would recognise them and it did. 

I am running from the firmware shell and using the boot cd command and then watching the output to see if it at least reads the cd. The output from the firmware when I try to load the cd says b[COLOR="Red"]oot cd DISK-LABEL: read of block0 failed cant open: cd[/COLOR] Which I find funny seeings my PC's drives recognise the disk easily enough no matter what OS Im running.

My experience with these particular tray loading drives is that they are finnicky about recognising cds. So my question is what is the best method for creating the cd from the ISO I downloaded on a PC  (I am using a PC because this is the only mac I have) My last attempt was using magic ISO maker on Windows but that did not do the trick. Has anyone else had the same problem?

I appreciate any help given.

---

### Post by 3rdalbum on 2006-08-03
A couple of things:

1. What happens when you boot up with the "c" key held down? That's the recommended method for booting from CD.

2. If you want the most compatible burn, use a CD-R that is designed for music, and burn it at 8x.

I have that exact same machine, and I've successfully burnt Ubuntu CDs that work on it.

---

### Post by stmiller on 2006-08-03
> use a CD-R that is designed for music

I find Maxell or Verbatim cds and dvds to be the most compatible. 

OT:
It is my understanding that one of music cds' difference vs plain cds is that part of the money goes to the RIAA, or to the record companies. Yuck! I avoid these at all costs.

[http://www.sweetwater.com/expert-center/techtips/d--08/01/2000](http://www.sweetwater.com/expert-center/techtips/d--08/01/2000)

---

### Post by Gossie on 2006-08-03
Sven04 and Gossie (me) have the same problem, but I don't have a tray loader, I think, it seems to me a standard cd rom drive.

[http://www.ubuntuforums.org/showthread.php?t=223752&page=1](http://www.ubuntuforums.org/showthread.php?t=223752&page=1) (Sven 04)

[http://www.ubuntuforums.org/showthread.php?t=223752&page=3](http://www.ubuntuforums.org/showthread.php?t=223752&page=3) (Gossie)

Help!
Gossie

---

### Post by electroconvulsive on 2006-08-05
Thanks 3rdalbum 
Firstly when I try to hold the c key down on booting It just simply boots to the firmware screen with the command prompt. The first message is  bootr unknown word. Upon this failure i tried the 2 other methods 1. mac-boot and 2. boot-cd.mac-boot just hangs and boot-cd returns an error message saying the disk is not recognised.Generally the drive doesnt recognise the burnt image.

I'll take your advice on the burning method and choice of cd but I have already ordered the cd from ubuntu. I will give it a go in the meantime and post the results here.

---

### Post by 3rdalbum on 2006-08-06
stmiller: If you've gotta give money to the RIAA to get your Mac to boot Ubuntu, so be it :-) Living in Australia I don't have that problem!

I actually haven't tried a downloaded Dapper CD in the iMac, only a burnt Breezy one and the Dapper ShipIt one.

A thought comes to mind: Try zapping the NVRAM. Hold down Command-Option-n-v while starting up the computer. If that doesn't work, try zapping the PRAM (I don't know how to do it on the iMac).

---

### Post by electroconvulsive on 2006-08-06
> **3rdalbum said:**
> stmiller: If you've gotta give money to the RIAA to get your Mac to boot Ubuntu, so be it :-) Living in Australia I don't have that problem!

I actually haven't tried a downloaded Dapper CD in the iMac, only a burnt Breezy one and the Dapper ShipIt one.

A thought comes to mind: Try zapping the NVRAM. Hold down Command-Option-n-v while starting up the computer. If that doesn't work, try zapping the PRAM (I don't know how to do it on the iMac).

Ok dude I burnt a cd that I managed to get to boot using the mac-boot command (the cd tray doesnt load the cd fast enough to boot this way). I have now run into more probz. After taking its time to boot the cd the system comes to the first command screen. If I try to boot it normally the kernel loads and then an error appears whilst it is trying to load the RAMdisk where it comes to a white screen and says [COLOR="Red"]failed to load the device tree chunk[/COLOR].

Ive sussed this out on launchpad and on these forums and as it stands thiis is happening to dapper and FC5 users with these particular machines and to date the bug remains unfixed. I might try a different distro on this machine. Im going to try to cancel the cd shipping from ubuntu now as trying to install it with the bug will be a waste of time. Thanks for trying to help or when a bug fix does come out I will try again.

If anyone comes up with a bug fix I can copile into the install disk please tell me. But for the moment it isnt happening at all.
[-( [-( [-(

---

### Post by Gossie on 2006-08-06
> **3rdalbum said:**
> A thought comes to mind: Try zapping the NVRAM. Hold down Command-Option-n-v while starting up the computer. If that doesn't work, try zapping the PRAM (I don't know how to do it on the iMac).

see [http://www.ubuntuforums.org/showpost.php?p=584714&postcount=10](http://www.ubuntuforums.org/showpost.php?p=584714&postcount=10) for P-ram:    Command-Option-P-R

---

### Post by 3rdalbum on 2006-08-07
I've also heard reports about that device tree chunk problem on iMacs, but funnily enough it doesn't happen on my machine.

You could always try Breezy?

---

### Post by jsonder on 2006-08-07
Is the cd being burned as an iso file?  

I had problems getting iso burns with some software programs that kept trying to put it into a data or audio format.

I know that this can be done easily with xcdroast.  Start with create a cd, put the iso file in, and then go to burn to burn it.

---

### Post by electroconvulsive on 2006-08-19
> **3rdalbum said:**
> I've also heard reports about that device tree chunk problem on iMacs, but funnily enough it doesn't happen on my machine.

You could always try Breezy?


Is your machine a G3 iMac? What speed? Have you figured out why yours installs Dapper no worries? Do you know if the developers are going to fix this bug in Edgy? Sorry my experiences with Breezy on a PC made me just a little wary of it. I am wondering what other distros I can install on this machine (without the bulldust I went through trying to install gentoo)
Tried installing Gentoo on this machine and the install process was a way too long and complicated process for me to bother with whilst working on my customers PCs so Gentoo is history to me.
I heaR THIS PROB EXISTS IN fc5 as well so Ill be giving that a miss.

---

### Post by electroconvulsive on 2006-08-26
> **3rdalbum said:**
> 
You could always try Breezy?

Yeah I tried breezy on PC and hated it. It was never ending dramas for me. Ignoring this self warning I tried Brezy Kubuntu on my mac and it was issue city (KDE has some serious issues and I should have got the gnome ubuntu)so I gave up on it. Dont ask how the gentoo installation went either.(that took a week and failed). Ive put the imac away for now and kinda am hoping that Edgy will have the problem fixed so I can install it but just for the moment im looking at buying a cheap G4 for my Ubuntu on mac experience. Here in Australia they go for around $100 AUD on ebay.

Thanks for the advice

---

### Post by Ububurns on 2006-08-27
Try using the Xubuntu 6.06 iso, and then install ubuntu-desktop.

I had many problems using the Ubuntu CD, and others have too.  Some have said that it's because the iso (702MB?) is too big, and some have mentioned other reasons.

Either way, using the Ubuntu CD didn't work, but using Xubuntu did.  Give it a shot!

---

