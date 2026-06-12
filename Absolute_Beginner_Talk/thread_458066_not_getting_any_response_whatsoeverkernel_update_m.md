---
title: "not getting any response whatsoever:kernel update might have killed something serious"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by SaddaGocaraRupa on 2007-05-29
so i updated the kernel on sunday, rebooted, and everything was fine. i then left it on for about 10 hours, went to bed, turned on my laptop and .... nothing. i'm getting neither grub, nor the centrino logo before grub or anything. 

here some tech specs:

asus z71v laptop
2 GB RAM
1.73GHz Pentium-M 740
Nvidia Geforce Go 6600

running FF and XP Home on a Dual boot...

so, first, when i turn it on, there's the familiar blue power light and the HDD light lights up for about 10 seconds and nothing else. my screen stays the blackest of blacks. 

i tried taking out my RAM and replacing it with a set that works, taking out my HDD and just running it off a live CD, blindly pressing 'del' and trying to change the boot order, which used to be 1. HDD, 2. CD/DVD drive and 3. Network (i think), but to no avail. when i put in the CD, it spins but otherwise nothing happens. my guess is that the cpu somehow got fried (i'd have no idea how) but then again i have no idea really. i don't think that the kernel update really had anything to do with the issue and suspect a hardware problem..it's just a weird coincidence

somebody help me please! i'm in the middle of an online degree and helpless without a computer...:(

thanks in advance!

-sadda

ps: i don't think it's my monitor cos i'd be able to hear my HDD do stuff if it would boot up without me seeing anything

---

### Post by starcraft.man on 2007-05-29
Uhhhhhh, *scratches head* I believe I have been mind boggled. I have never heard of a kernel update killing a machine (highly doubt it did anyway), even if it was incompatible, the old kernel is left behind and you should still get GRUB, and nothing should prevent your manufacturers logo. I uh, think your labtop spontaneously died... sorry >.>. 

Unless someone else has a thought on this... I mean if you can't even get the live CD to boot or get in the bios, that computer is hosed.

---

### Post by mozetti on 2007-05-29
How far are you getting? Is the laptop able to POST (power-on self-test) where it counts the RAM and probes for your hard drives and cd/dvd drives?

If you're not getting to the Centrino logo, which is usually an overlay on the POST process and part of the BIOS, then you have a hardware problem. Most likely it's a bad motherboard, but RAM or the chip could be the culprit, too. Either way, a kernel update isn't responsible.

One of my friends had the same thing happen to his Toshiba laptop when he replaced his RAM -- he zapped the motherboard somehow and have to get it replaced.

Good luck.

---

### Post by starcraft.man on 2007-05-29
Uh, he already said he took a known good source of ram and tried that and it didn't work... so I guess it is the mobo. That really sucks. Might be time to just pack it in and get a new labtop, or if you can replace the mobo (might be somewhat costly, and you never know it could still fail after replacement, I seen it happen). If your in the states though, you now have the option of buying a labtop with Ubuntu :). You could of course always move over your data assuming the drive didn't fail to the new comp.

Just a thought, sometimes when a computer dies... it just doesn't want to come back to life, and we have to give it its final rights and move on :p.

---

### Post by george29 on 2007-05-29
> **starcraft.man said:**
> If your in the states though, you now have the option of buying a labtop with Ubuntu :). You could of course always move over your data assuming the drive didn't fail to the new comp.

Just a thought, sometimes when a computer dies... it just doesn't want to come back to life, and we have to give it its final rights and move on :p.

you can also get a laptop with ubuntu pre-installed here in the uk....

[http://efficientpc.co.uk](http://efficientpc.co.uk)

they seem worth taking a look at apart from the awful selection of stargate names for the machines they supply!

---

### Post by SaddaGocaraRupa on 2007-05-29
aarrgh...not the kind of answers i was looking for, but thanks anyway. yeah, i thinks it's either the mob or the cpu..it's a barebone machine, so theoretically, if it IS the cpu, i could just pop it out and replace it easily. if it's the mobo, i'm not gonna bother and just get a new one. i live in japan, so neither option is on, but installing ubuntu is so easy,  i might just get a mac this time and dual or maybe even triple boot it :) 

anyone had any experience with a fried cpu? what happens? does the machine still power up?

i'm not getting a RAM count, but, yea, i replace the RAM and it did nothing. however, i don't have a spare cpu lying around. i7ll take it to geek town and go from shop to shop. thanks everyone

---

### Post by ubz on 2007-05-29
Maybe this will help.  Remove the laptop battery put it back in and try to boot.

---

### Post by SaddaGocaraRupa on 2007-05-31
well, i tried that but it didn't work :( 

hmmm...i'll just return it to the manufacturer when i get back to Australia next year...

---

### Post by SaddaGocaraRupa on 2008-04-11
well, i'm back. took a year, but the machine is fixed. it was the GPU. now i'm all updated can't believe how much progress was made from beryl to compiz fusion. great work, to all involved!!!:KS:KS

cheers,

-sadda

---

