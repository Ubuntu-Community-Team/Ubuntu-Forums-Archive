---
title: "Ubunto Won't Install Following Power Outage"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by DaveySpeedstar on 2008-04-14
I’m trying to install Ubuntu on an old machine (Pentium 3 processor).  I naturally followed all the instructions, however while partitioning the hard disk, we suffered a power cut!!!

Since then I have tried to start the install process again (and again), yet I am unable to get beyond the 2nd install screen (2 of 7).

This is my first time with any Linux system, and I have limited computer knowledge.  I have read the stickies on here as well as the installation/starter guides, but can’t see anything relevant to me.

If I’m missing something I would be really grateful if someone could nudge me in the right direction.

---

### Post by caravel on 2008-04-14
Does this machine have any valuable data on it?  If not then try booting to the livecd and doing sudo gparted from the terminal and delete all partitions and start again from afresh.

---

### Post by Trail on 2008-04-14
Sorry, care to remind us which one is the "2nd install screen (2 of 7)"? :)

---

### Post by DaveySpeedstar on 2008-04-14
> **caravel said:**
> Does this machine have any valuable data on it?  If not then try booting to the livecd and doing sudo gparted from the terminal and delete all partitions and start again from afresh.

I brought the tower with the specific intention of using it to play with Ubuntu.  The only thing it has on is a very old very pirated version of XP-Pro.

I'm at work atm and will have a look at doing sudo gparted from the terminal when I get home.

I assume that this option will be obvious from the start-up menu, if not I would be grateful if you could give me a blow by blow guide as to how to do it (else show me a link).

I'm really grateful for this I wasn't expecting a reply so quickly

Oh - the 2nd screen is the map of the world which asks you to point to where you live and which time zone you're in.

Thanks again folks - as soon as I get my head round this I'll try to be more help than a hindrance

---

### Post by DaveySpeedstar on 2008-04-14
I might be over-complicating things here but I assume that I need to do [this](https://wiki.ubuntu.com/gparted).

After opening the command line  [like this](https://help.ubuntu.com/7.10/basic-commands/C/starting-terminal.html).

---

### Post by ScorpKing on 2008-04-14
Always use gksudo or kdesudo when running GUI apps as root. Just plain sudo will give you a lot of headaches.

---

### Post by |{urse on 2008-04-14
would be nice as trail said to be reminded which screen is 2 of 7. And was the power cut a cut or a surge, that definitely would clear things up a bit considering that if the cpu, ram, cd rom were not affected by the surge but the hard drive were damaged you would boot to a livecd that could not install.

---

### Post by DaveySpeedstar on 2008-04-14
> **DaveySpeedstar said:**
> the 2nd screen is the map of the world which asks you to point to where you live and which time zone you're in.

Everything else (HD cpu etc etc) seems to be working fine, as it boots, runs and defrags in Windows OK

---

### Post by Trail on 2008-04-14
Umm, how far did the installer go?

The only thing I can think of, which is probably wrong, is that the installation did proceed far enough that you can boot from it, and you are booting from the hard disk instead of the live cd. As far as I know, the installer is copied on your hard disk first, then removed towards the end of the installation, which would explain why you could see it on your desktop.

I see no other reason why a **live-cd** would fail to get past the timezone screen while it did before. Booting from a half-finished hard disk installation is my only (probably wrong) guess.

---

### Post by DaveySpeedstar on 2008-04-14
originally the installation was a couple of minutes into partitioning the hard drive.

I have since gone into windows and windows loads up fine, although there is no indication that Unbunto is on the HD.

To be honest I 'feel' that id I can 'unpartition' the HD, I could start over.  Is this possible?

When I test the CD, it says there are no faults. However could burning a new CD help? (I 'feel' not).

Maybe  trying a different Ubunto release?

---

### Post by Trail on 2008-04-15
Yes, you can start over.

---

### Post by DaveySpeedstar on 2008-04-15
Brilliant - thanks very much for your help...

So to be perfectly clear I go into the gparted screen, find the command to delete the partition(s), and once I've deleted the partition I can reboot and try again

---

### Post by Trail on 2008-04-15
Yes, except you don't need to reboot; delete the partionions, and in the free space select "Make New Partition".

---

### Post by DaveySpeedstar on 2008-04-15
Do I need to be connected to the intenet???

I've just read elsewhere that I should be connected to the internet when installing Ubuntu.  If this is the case This might be where I've been going wrong.  The first time I tried installing I was connected to the web, since then I haven't.

---

### Post by |{urse on 2008-04-15
lol nice website. Rollerbladers are awesome, we used to throw sticks in front of those guys. :) You don't need to be connected to the internet when you install ubuntu. Just imagine if everytime ubuntu didnt install a bcmwl driver the installation wouldnt continue. lol, that would be terrrfying.

---

### Post by DaveySpeedstar on 2008-04-17
I got this sorted out last night.  Gutsy just wasn't going onto my computer - it was still stalling at the 'Where in the World' screen.

I downloaded Hardy (8.04) at that went straight on without any problems!!!

My next problem is connecting to the internet using a Fujitsu FDX310 USB modem.  I may (will) be back for more advice very soon

---

