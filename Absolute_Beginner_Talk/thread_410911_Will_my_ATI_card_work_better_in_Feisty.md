---
title: "Will my ATI card work better in Feisty?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-16
I am just wondering if my ATI card would be easier to install in Feisty than in the Edge i use now. I need to install my system since i have changed to ATI card since i got it for a good price. So i am just waiting for Feisty to be released. Its the 19 this month its going to be released right?

---

### Post by bwhite82 on 2007-04-16
From my personal experience, installing/using Feisty, it is not any easier for us ATI users. Being on Linux for a number of months has led me to become the newest Nvidia fanboy. I will be dropping ATI like a bad habit as soon as I can, I would recommend you do the same. Until you do, there is still hope, however, in the form of countless hours spent digging through forum posts and wikis. Good luck.

---

### Post by daynah on 2007-04-16
You will be able to upgrade to Feisty without having to reinstall your ATI drivers (if al goes well, if all doesn't well, you wont lose data, you just will have to reinstall the drivers).

I am an Ex-ATI also. With an ATI card you can do what you need to do to get around, or most people can, but you can't do the fancy stuff like Beryl (search for it  on youtube to see it). I got very jealous of my friend's Beryl, so I used my $40 tax refund to get a new Nvidia card and it works great, I didn't need anything more, and I have SVideo out, and a DVI port for future dual monitoring.

I really needed to switch though. I had the one ATI card that was "least" supported (that's the terminology used... ugm). The drivers would work for a few days and then freeze my computer. I tested the memory, the hard drive... was even about to go to the store to get my power supply tested. But my friend said he thought it might be my video card, and when I looked up the support status, decided I wanted beryl and got a new card, all the freezing stopped. :)

Since you haven't complained of freezing, I doubt you have the awful card I do. But just know that ATI has given linux minimum diver support and  does not plan to make this any better. They've made a formal announcement that there are no plans to fix everything that's wrong.

$40 will fix it. If you do get a new card, make sure to look up whether you're AGP or PCI (cough, I flubbed that up).

Have fun sweetie!

---

### Post by jvc26 on 2007-04-16
My ATI card wasnt the easiest to set up in Feisty - well it wasnt any easier than it was in dapper, or in edgy over the time I've used Ubuntu. I have beryl working fine with very little slowdown which is nice, though as beryl is on the buggy side with some things, some of the odd issues may well be down to that. It is easier to get an nvidia card as the support across the board is much better, and when I have the money I may switch my card. If you can get some support for your ati card to be honest it isnt really worth the switch, but if you can then go for it. I set up mine on feisty using the instructions [here]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") - its still old xorg.conf playing to get it working properly. And presuming its released on time, feisty final will be released on the 19th.
Il

---

### Post by U5tabil on 2007-04-16
Well ok.

But the thing is that i just purchased a Sapphire X1950 Pro 512MB AGP card. Because i need to have a card to play games with and since thats the best for AGP and that i got it for half the normal price i did buy that one. But i have a Geforce 5600XT 128MB AGP card that i am using rigth now in Edgy, Since my ATI card failes totaly. And that i need to reset stuff to make stuff work again. So i am only waiting for the release so that i can make a new instaltion on the pc. 

I am using Linux to watch movies, surf the nett, chat, and downloading.
Then i have a other harddrive a WD Raptor disk that i have windows on that i only uses to play on nothing more.

So for now i need to swap between cards when i want to play :tongue: 
But thats not a big problem since i dont have more space to more harddrives i need to swap them aswell. I am waiting for a IDE controller to fix that problem.
1x IDE 320Gb Seagate
1x SATA 320Gb Seagate
1x IDE 120Gb WD
1x IDE 80Gb WD
1x IDE 20Gb WD
1x SATA 74Gb WD Raptor

:lolflag:

---

### Post by TimelessRogue on 2007-04-16
Hmmm ... I've got an ATI Radeon 9700 installed in my desktop that has worked perfectly from the get-go with both Dapper and Edgy.  I upgraded to Feisty (using "apt-get update" and then "apt-get upgrade" after changing my sources.list to reference the Feisty repositories followed by Synaptic) with my laptop (HP n5000) last night and experienced no problems and am planning to do the same with the desktop either this evening or tomorrow.  I'll let you know how it goes ... tho I don't anticipate any problems ...

---

### Post by U5tabil on 2007-04-16
> **TimelessRogue said:**
> Hmmm ... I've got an ATI Radeon 9700 installed in my desktop that has worked perfectly from the get-go with both Dapper and Edgy.  I upgraded to Feisty (using "apt-get update" and then "apt-get upgrade" after changing my sources.list to reference the Feisty repositories followed by Synaptic) with my laptop (HP n5000) last night and experienced no problems and am planning to do the same with the desktop either this evening or tomorrow.  I'll let you know how it goes ... tho I don't anticipate any problems ...

YEs thank you that would be nice. I think i will try anyway when the new festy is released.

---

### Post by felipefrog on 2007-04-16
I remember edgy livecd wouldn't even start with my ATI 9600 on, so I had to switch to a nvidia, install, and later switch back to ATI with vesa mode on and start digging forums to install decent drivers (now I have beryl, etc).

I just hope I won't have the same problems when upgradind to Feisty!

---

### Post by U5tabil on 2007-04-16
how do i exactly turn on vesa driver? i have my geforce card in now and my lovly looking ATI card beside my pc.

---

### Post by thesphine on 2007-04-17
I had a similar problem when I first installed Dapper - I ended up using the alternative install CD to avoid booting into X until I'd swapped onto the vesa driver to allow me some breathing space (complicated by the vesa driver not recognising the DPMS from my monitor and using a resolution and refresh rate that it didn't support)

Using the fglrx driver fixed all this - however - it all came back when I upgraded to feisty as the fglrx driver in feisty no longer supports the older ATI cards - so beware ! I eventually tracked down my problem to the AGP Graphics Apeture size in the BIOS of my machine. 

In short - try swapping to the OSS Radeon driver before you upgrade to feisty - if it doesn't break your system you'll be fine. Probably.

---

### Post by U5tabil on 2007-04-20
> **U5tabil said:**
> how do i exactly turn on vesa driver? i have my geforce card in now and my lovly looking ATI card beside my pc.

How do i do this? I am going to make a totaly new installation with feisty fawn today, so if it rejects my card then what? shall i turn on vesa driver then? but how do i do that?

---

