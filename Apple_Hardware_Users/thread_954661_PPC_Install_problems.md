---
title: "PPC Install problems"
date: 2008-10-21
forum: Apple Hardware Users
---

### Post by GazHay on 2008-10-21
Trying to install fresh ubuntu server onto a b&w g3.

It is already running a xubuntu install from a previous install.

I have burnt, Desktop 7.1, Server 8, Server 7.1 and Server 6.06.2 using 2 different Macs with 2 different burners, at slowest speeds with images that passed md5 checks.

I have tried 4 different optical drives with different IDE cables and configurations in the b&w g3.

Every time I try any install of a server based edition, I get as far as it trying to copy some of the apt packages off the cd and fails the cd check. 

If I do an integrity check it always fails (at ppc/packages)

Any ideas? I'm fresh out - and I already trashed the xubuntu partition cos I was trying to do a server install with a softraid.

---

### Post by GazHay on 2008-10-21
Is it possible for me to modify the cd img to not do the integrity check and just batter on with the install?

Or is there a problem with all PPC images? I'm obviously missing something because I can't explain the problem unless all PPC disk images are broken - which they can't be as others have used them, including myself in the past!

help :(

---

### Post by tiresia on 2008-10-21
Can you now start with a desktop CD? I mean, do you have this problem just with the server edition?
Have you added some extra cards in the last time (Grafic Card, USB Card)?
To check if your issue is related to your CDs or to your hardware, can you try them with another Mac.
Which CDs are you using?

---

### Post by Concorde105 on 2008-10-21
My desktop PPC image worked fine on my PowerBook... Though it is a 2005 G4... Dunno what could be wrong, maybe bad cd burner?

---

### Post by GazHay on 2008-10-22
The desktop 7 disk i have gets into the live cd and will let me do that.
Ideally I wanted to implement softraid at install time, and gparted on the live disk doesn't seem to want to let me do that which is why i opted for server disks.

I've tried different burners, different macs to burn, and even different optical drives in the target mac, along with changing ide configs within it too.

Am at my wits end!
Guess I'm going to have to install a desktop and work backwards to remove the gui!
Maybe forget about the softraid too

---

### Post by GazHay on 2008-10-22
I have just reviewed his problem.

It seems that EVERY burnt disk fails at ./dists/dapper/main/debian-installer/binary-powerpc/Packages.gz - failing the md5 check. (or similar - obv. not every one is dapper)

However, the md5 for the disks seems fine and several burners burn the disks the same (i've re-imaged them and md5ed the results)

Could this be a hidden RAM disk issue? - as this is before I partition or setup disks - is the installer trying to copy stuff to a RAM disk at this point? I have 512MB in the machine so I thought I was safe, I can bump in some spare RAM and see if that helps.

---

### Post by tiresia on 2008-10-22
> **GazHay said:**
> Guess I'm going to have to install a desktop and work backwards to remove the gui!
You don't need that. You can download a MinimalCD and choose the configuration according to your needs (without X) when you install the system
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by GazHay on 2008-10-22
> **GazHay said:**
> I
It seems that EVERY burnt disk fails at ./dists/dapper/main/debian-installer/binary-powerpc/Packages.gz 

/dists/hardy/main/debian-installer/binary-powerpc/Packages.gz

for server 8 disks.

It seems strange that if the multiple burners were to blame, or the cd images (which were downloaded independently and md5 on different machine and verified as correct) would fail at the exact same step, and the cds fail the integrity check at the exact same point.

What's worse, I can't even make the 7 live cd boot now so I am stuck - probably have to go back to OSX/9 :/

unless I can dig out some netboot instructions

---

### Post by tiresia on 2008-10-22
Do you have any extra PCI Card?
You can try now resetting your VRAM/PRAM (hold down at boot up cmd+opt+P+R)
And, another way is to try with a USB Stick
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

### Post by GazHay on 2008-10-22
Problem found.

It's either the logic board or the chipset firmware.
I've had OSX on it so I doubt it's the firmware - guess the MLB is dying.
(I happened to have another B&W g3 - so i'm going to set it up identically and install then transfer most of the hardware back to the older box and see if it boots!)

---

### Post by graphicman21 on 2008-10-22
Hi. I am having trouble installing Ubuntu Linux on a Sawtooth Power Macintosh G4, upgraded to 1.6 GHz processor, with 640 MB RAM, and Mac OS X 10.4.11 Tiger, and a Radeon 9800 Pro Mac Edition graphics card (I no longer can run Classic OS9 mode because of compatibility issues with my new graphics card, which is only OS X-compatible). let me explain my problem...

I have both Hardy Heron and Gutsy Gibbon. I tried installing both on my computer. I can never get to even the Ubuntu Logo splash screen. These discs were both burned on Nero from my dual-core Pentium processor-powered PC because I don't have my own burner for my Mac. I just have an internal DVD-RAM cartridge drive, and no internal or external CD/DVD burner. 

I am not sure why it does not boot up all the way, and they are both PowerPC distros. But, I do I admit, I am a total "noob" (lol)  when it comes to these sorts of things. Is there anything that I am doing wrong here? Are there any tips you can give me? Is there anything else I need to install for Mac? Could it be that the fact I burned the discs on a PC may be a problem? Sorry for all the questions, but I am just insatiably curious about this dilemma that I am having.

Your assistance is duly appreciated. Thanks.

---

### Post by GazHay on 2008-10-23
Sorry to bump,

all my install media crashes while partitioning a softraid.

Is it not possible to use a softraid at install on PPC?

I've spent almost 3 days trying to get this thing going, tempted to try a fedora or suse install before just biting the bullet and using non-raided disks!

---

### Post by Frak on 2008-10-23
> **graphicman21 said:**
> Hi. I am having trouble installing Ubuntu Linux on a Sawtooth Power Macintosh G4, upgraded to 1.6 GHz processor, with 640 MB RAM, and Mac OS X 10.4.11 Tiger, and a Radeon 9800 Pro Mac Edition graphics card (I no longer can run Classic OS9 mode because of compatibility issues with my new graphics card, which is only OS X-compatible). let me explain my problem...

I have both Hardy Heron and Gutsy Gibbon. I tried installing both on my computer. I can never get to even the Ubuntu Logo splash screen. These discs were both burned on Nero from my dual-core Pentium processor-powered PC because I don't have my own burner for my Mac. I just have an internal DVD-RAM cartridge drive, and no internal or external CD/DVD burner. 

I am not sure why it does not boot up all the way, and they are both PowerPC distros. But, I do I admit, I am a total "noob" (lol)  when it comes to these sorts of things. Is there anything that I am doing wrong here? Are there any tips you can give me? Is there anything else I need to install for Mac? Could it be that the fact I burned the discs on a PC may be a problem? Sorry for all the questions, but I am just insatiably curious about this dilemma that I am having.

Your assistance is duly appreciated. Thanks.
While it's not helping to solve your problem, my Sawtooth works fine with just about any CD/DVD drive I put in it (it is a HP DVD Writer 1040d). Even supports lightscribe through some LaCie drivers. Drives are fairly cheap (about $30-$40), you might looking for one. Also, happens to be that my sawtooth isn't revision 0003, so it can use a Dual card.

EDIT
Just thought, you'll have to use patchburn, but that's a 1 time not-so-inconvenience.

---

### Post by DRM_free on 2008-10-24
To check whether a CD is good, insert it into another computer running Linux (it can be any old PC) and run the "md5sum md5sum.txt &> results.log"

Then look at the newly created results.log file and see if there are any corrupt files. If there aren't, then the CD is fine.

---

### Post by GazHay on 2008-10-24
> **DRM_free said:**
> To check whether a CD is good, insert it into another computer running Linux (it can be any old PC) and run the "md5sum md5sum.txt &> results.log"

Then look at the newly created results.log file and see if there are any corrupt files. If there aren't, then the CD is fine.

Was this aimed at my problem?

---

### Post by GazHay on 2008-10-24
Sadly looks like it was dodgy RAM all along.
I have removed the 256MB chip that I suspect is causing problems and have finally got past partitioning (though not with a RAID) if this works, I'll try the raid again.

---

### Post by stream303 on 2008-10-27
With those old boxes, be sure to burn the CD at ridiculously low speeds, such as 1x or 2x...

---

### Post by Kopachris on 2008-10-27
Edgy Eft installed fine for me, except for the part about leaving my OS X partition intact (since Ubuntu doesn't (didn't) support HFS+).  Gutsy Gibbon, on the other hand, would not even boot to the LiveCD.

---

### Post by Frak on 2008-10-27
Question, does it mount to the desktop? When I got my Sawtooth, it could only read CD-R, CD-RW, and DVD+R. Mind the **+**

---

### Post by GazHay on 2008-10-28
> **stream303 said:**
> With those old boxes, be sure to burn the CD at ridiculously low speeds, such as 1x or 2x...

As I mentioned in my original post.


Well, I got the install working (it was hosed RAM).

However, I couldn't make a PPC boot off a "new world" boot parition and then switch to the multi-disk I had setup during the install.

Probably just a grub/yaboot problem - but I don't know enough about either to make it work, and I'm a week behind with this box, so am just going to fire on ahead - I'll maybe try again when I have more time.

---

