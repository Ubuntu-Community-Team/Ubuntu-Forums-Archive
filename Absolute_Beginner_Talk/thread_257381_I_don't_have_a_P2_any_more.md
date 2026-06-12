---
title: "I don't have a P2 any more"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Claptrap on 2006-09-14
but I thought about trying to install Ubuntu into my present computer, into my second HDD (IDE), which is in retractable caddy. My OS is XP Home, installed in SATA drive. My processor is 64 bit Athlon 3200, but my friend's machine is a second hand one with the old 32 bit Athlon 1.3 GH - does that matter? I thnik the Ubuntu is for 32 bit processors. :)

1. I would like to keep these two OSs in totally separate Hard drives, not least because I'm planning to give the drive to my friend, how do I determine where Ubuntu installs itself, will the Grub install in there also?

2. How do I set up the pc to dual boot?

The spare HDD should have FAT32 formatting (but be otherwise empty) should I do anything about that?

3. Do the drivers need linux installations? Most of the hard  ware is so old it might be difficult to find them.

3. My friend's PC is of course very different from mine: do I need to do a complete uninstall/reinstall when giving the drive to my friend?

4. Maybe there is a way to have both Ubuntu AND windows open at the same time (given the proceesing power is the good enough)?

As you can see, I'm quite a novice in computers generally, so please don't assume I know how to format a drive or even more common knowledge.

---

### Post by bodhi.zazen on 2006-09-14
1. No problem. You will select where to install at time of install.

2. When you install you will install GRUB into the MBR and each time you boot you will be given a choice of which OS to run.

Formatting of spare HD is irrelevant as you should re-format it as you install Ubuntu.

3. In general Linux runs fine on older hardware.

3. (Or should that be 4.) Yes you will have to re-install if you move the HD between boxes.

4. No and yes. You have to bot one or the other. You can run qemu or vmware on either Linux or Windows.

If you are a novice you will be fine. Worst thing that can happen is you will need to re-install your OS (Windows). Back up you data!!!!!!!!!!!!

Otherwise you will be on a steep learning curve for a few weeks/months.

Start here:

[ Unofficial Ubuntu 6.06 (Dapper Drake) Linux Starter Guide](http://ubuntuguide.org/wiki/Dapper)

[Ubuntu wiki](https://wiki.ubuntu.com/)

---

### Post by daller on 2006-09-14
Do NOT install Ubuntu on the HD before giving it to your friend!

It's quite likely, that NOTHING will work!

Give him the drive, and install it on HIS computer instead!

About the drivers! - Almost everything "old" is supported!

About FAT32 - Ubuntu will format it into EXT3 (a linux filesystem) - The installation will also detect Windows on the other drive, which means that the only thing you have to be aware of, is that you choose the right HD during installation! (Not the Windows HD!)

---

### Post by Iowan on 2006-09-14
> **daller said:**
> **EDIT: BTW: Ugly avatar :D (like mine... I know! :D)**

**EDIT2: How have you managed to post more than 800 posts, and still be a newbie?**

Are you addressing **Claptrap **or **bodhi.zazen**?
Time for EDIT3?  :-\"

---

### Post by bodhi.zazen on 2006-09-14
> **daller said:**
> **EDIT: BTW: (Edit3: bodhi.zazen) Ugly avatar :D (like mine... I know! :D)**[/B]

Thanks I aim to please. I did see Edit2: Linux hurts hurts my brain.

---

### Post by Claptrap on 2006-12-31
Thanks guys. It turned out that my ex boyfriend had swapped the HDD with his measly 1GB one so the project is off again. I must have something like Ubuntu which is user friendly enough for a beginner (once I've struggled to set it up) - some of the smaller versions, like puppy linux just won't do. 

It looks like I have to put Linux on the back burner, until I do have the time and money (to obtain another drive).  That could take some while... But latest when MS stops supporting XP - and I have a feeling it will be pretty soon, to force people to take up Vista that no-one wants - I will jump to linux side.

---

### Post by MkfIbK7a on 2006-12-31
one gig hardrive where on earth could someone get somehthing like that?:?

---

### Post by daller on 2007-01-01
> **Claptrap said:**
> Thanks guys. It turned out that my ex boyfriend had swapped the HDD with his measly 1GB one so the project is off again. I must have something like Ubuntu which is user friendly enough for a beginner (once I've struggled to set it up) - some of the smaller versions, like puppy linux just won't do. 

It looks like I have to put Linux on the back burner, until I do have the time and money (to obtain another drive).  That could take some while... But latest when MS stops supporting XP - and I have a feeling it will be pretty soon, to force people to take up Vista that no-one wants - I will jump to linux side.

Take up the challenge, and jump now? (install aside Windows, or simple wipe the disc?)

---

### Post by STREETURCHINE on 2007-01-01
> **wert613 said:**
> one gig hardrive where on earth could someone get somehthing like that?:?

i have three of them in the cupboard,you can have.lol   :D

---

### Post by gn2 on 2007-01-01
> **STREETURCHINE said:**
> i have three of them in the cupboard,you can have.lol   :D

I'll have them if you'll pay the postage! ;) 

It's scary how fast hardware becomes redundant, I'm typing this on a Toshiba Portege 3440CT, P3 500, 192mb RAM which cost £2000 new in 2000.

Seven years on and it's still working as well or better (faster hard drive) than new, but it would be seen as being an antique now and they're available on eBay for as little as £80.
I got this one just over a year ago for £150 (with three month warranty and lots accessories)

I have also put an old Dell GX110 SFF PC to use as a dedicated (Amarok) music jukebox in my living room, total cost for rebuilding it with 40gb notebook drive, silent 5v CPU cooler, 10" TFT and USB sound card £125. My Zalman fanmate PSU modification works, but proceed with caution ......

There's plenty life left in old hardware, and Linux breathes it back in.

---

