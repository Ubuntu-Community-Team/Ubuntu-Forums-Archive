---
title: "Recoverying back to XP"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by StephanGFX on 2007-07-10
So I have had Ubuntu for a few days now, and I miss my XP extremely bad. So I need to know some stuff before I start.

I have an HP with Windows XP Media Center Edition installed on it. That was before I installed Ubuntu. When I start up the computer, It gives me the option to go to the recovery console. It does a whole bunch of stuff and restores Media Center. Supposedly. I'm not sure if this will work though, because  I installed a new OS (Linux from Ubuntu). My original plan was to dual boot linux and xp, but somehow ubuntu ended up taking over my whole computer hdd and I lost all my xp memory and only had ubuntu. So I don't even know if it will install xp from the recovery console or anything. Can someone give me advise, and tell me how I can make this as noob proof as possible? because I paid a pretty penny for my computer, and I don't want to see it go down the drain. 

Thanx

---

### Post by regomodo on 2007-07-10
> **StephanGFX said:**
>  When I start up the computer, It gives me the option to go to the recovery console. It does a whole bunch of stuff and restores Media Center. 

Thanx

I don't understand what you mean by this. Do you mean when you select Media center it starts up? If so it's a piece of piss to sort out.

Use the live cd to edit your partitons and use gparted to remove the Ubuntu partition

---

### Post by desheikh on 2007-07-10
Hi,

When your installing ubuntu you have an option to either format your entire drive and do a clean install or create an extra partition to install ubuntu on. You should pick the latter if you want to dual boot. The first partition will do exactly what it says, format everthing!

Im not sure if the format includes the recovery partition stored on your computer. As far as I remember I had to manually erase mine. Its wasted space in my opinion since you can always use the install cd (you did get an xp install cs didnt you?) Just try out the recovery option and see if it works. If not then just install XP from the cd and then you can install ubuntu again. Just dont pick the format my drive option this time around :)

Desheikh

---

### Post by StephanGFX on 2007-07-10
well right when i turn on my computer it shows the hp logo with a blue bg and it says press f12 for recovery console. i've used it before when i had somekind of system crach on my xp. but my windows xp got completely erased when i tryed to install unbuntu through dual boot. so if i delete ubuntu i wont have an os installed. and i didnt get a cd with my computer

---

### Post by regomodo on 2007-07-10
I doubt that has anything to do with hard drives. I guess that's the motherboard utility.

What i am talking about is the grub boot screen (i assume you know what that is). Is there an xp option?

---

### Post by StephanGFX on 2007-07-10
no there is not an option to boot xp in the grub menu. xp was erased. I even looked at my hdd and it told me that i have 221gb out of 250gb left. and when i was on my xp i only had 32gb left.

---

### Post by FuturePilot on 2007-07-10
It looks like you chose the option to format the entire drive. In that case it also wiped out the recovery partition as well. The best advice I can give is to call HP and see if they will send you a set of recovery CDs.

---

### Post by RedRat on 2007-07-10
I think you might be screwed. I did exactly the same thing with both Ubuntu and PClinuxOS. For me, it was no great loss of XP since my XP hard drive crashed and I did a virgin install on a brand new HD. I wanted a dual boot also but hit the wrong selection. I too would like to have XP on this computer as a fall back. However, the more I use Ubuntu the more I like it. I am running this on an old Dell Dimension 4100 that is about 7 years old and Linux is far, far snappier. 

I think the only thing you can do is to get the Install CD for XP or Media Center whatever you have and do an install. Since I am a Newbie also, I would sure like to know how to do that safely. At one time, I think with the older Windows 2000, it had to be installed on the first or boot partition but I think XP can be installed anywhere on the Disk. 

Does anyone have any ideas how to put XP on the Ubuntu disk. I have plenty of room, about 140 GB that can be shrunk down.

---

### Post by StephanGFX on 2007-07-10
well this is what it says on the hp support site:


Where can I get recovery CDs?

HP Media Center computers that ship with Windows XP do not come with recovery CDs. Instead, they use a hidden space (partition) on the hard drive to store the recovery information. Using a hidden partition provides a more convenient, more stable recovery process that eliminates the need for CDs that can be scratched or lost.

Does that mean that my partition for my recovory console didnt get affected?

---

### Post by Feba on 2007-07-10
yep- your HP 'recovery' was a partition on the hard drive, which you destroyed. You're either going to have to try to weasel a recovery CD out of HP, buy a new copy of XP, or learn to live with linux.

No offense, but you really did bring this on yourself by being careless.


EDIT: To be precise, you destroyed the partition, not the hard drive. You formatted the hard drive. Remember when you were a little kid and you decided to try what that "format" button on your playstation did to your memory card? This is the same way, except it makes adults cry too.

---

### Post by FuturePilot on 2007-07-10
It's gone. If you did in fact choose the format all, it formated everything. On my HP computer there was a thing in Windows where you could create recovery CDs. They come in handy even though I have a recovery partition as well as I have managed once to mess everything up and had to start completely from scratch.

---

### Post by regomodo on 2007-07-10
oh dear. Somebody was in a rush then. You won't do that again

---

### Post by regomodo on 2007-07-10
> **RedRat said:**
> I think you might be screwed. I did exactly the same thing with both Ubuntu and PClinuxOS. For me, it was no great loss of XP since my XP hard drive crashed and I did a virgin install on a brand new HD. I wanted a dual boot also but hit the wrong selection. I too would like to have XP on this computer as a fall back. However, the more I use Ubuntu the more I like it. I am running this on an old Dell Dimension 4100 that is about 7 years old and Linux is far, far snappier. 

I think the only thing you can do is to get the Install CD for XP or Media Center whatever you have and do an install. Since I am a Newbie also, I would sure like to know how to do that safely. At one time, I think with the older Windows 2000, it had to be installed on the first or boot partition but I think XP can be installed anywhere on the Disk. 

Does anyone have any ideas how to put XP on the Ubuntu disk. I have plenty of room, about 140 GB that can be shrunk down.

Yep, you can do that but you'll have to reconfigure grub. I've done it  afew times, it's fairly simple, but can't remember right now. It's 4:15am

---

### Post by kvonb on 2007-07-10
:lolflag: Feba :)

> **Feba said:**
> 
No offense, but you really did bring this on yourself by being careless.


EDIT: To be precise, you destroyed the partition, not the hard drive. You formatted the hard drive. Remember when you were a little kid and you decided to try what that "format" button on your playstation did to your memory card? This is the same way, except it makes adults cry too.

---

