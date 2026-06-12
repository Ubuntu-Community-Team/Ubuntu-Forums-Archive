---
title: "Dual Booting Ubuntu and Windows XP"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Optic on 2006-04-14
Hey guys, I'm hoping you're a friendly bunch so that I don't make myself some enemies:-#  but I want to Dual Boot my laptop to run Ubuntu and Windows XP.

It's got Windows XP in it, and I want to put Ubuntu in my D: -

[img]http://img131.imageshack.us/img131/7097/cop2wn.gif[/img]
Since it has a large capacity and is empty. I'm sure I could do it without messing everything up since everything's in my C:

I put in the installation disc and I was baffled, I was kinda scared too, I don't have a backup of XP so I don't want to be left with an un-useable system.

I don't know if I was to run it in Expert mode or anything, but some help would be appreciated greatly.

Thanks guys,
](*,)

---

### Post by dermotti on 2006-04-14
Just jot down the drive sizes of both your drives and put it on the one that matches the drive space of drive D:

---

### Post by mrchrisblau on 2006-04-14
Put in the disc. Reboot and go into the bios, make sure the disc boots first.

Boot up, should run from disc (and not xp).

Then follow this great guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The only tough time I had was around partitioning... but if you follow the guide EXACTLY, you'll be ok.

However, I wouldn't reccomend doing it on a box with data that you don't want to lose. Perhaps back up the important stuff onto discs first? Its your call in the end of course, but just seems risky to me.

Good luck!

---

### Post by theaffman on 2006-04-14
Doesn't that drive hold the backup information for if you have to reinstall xp?

---

### Post by mrchrisblau on 2006-04-14
[QUOTE=theaffman]Doesn't that drive hold the backup information for if you have to reinstall xp?[/QUOTE]

That would depend on what he has on there...

---

### Post by theaffman on 2006-04-14
Your right. 
optic did you just delete the contents of that drive? or did you install your own copy of xp?

---

### Post by brainfry on 2006-04-14
My Acer laptop has a hidden partition at the start of the drive which enables diskless recovery of the XP system if something goes wrong. 
When I put Breezy on it, I went into disk management under XP, deleted drive D, rebooted and then partitoned the free space during the install.
Hope this helps.

---

### Post by Optic on 2006-04-14
[QUOTE=theaffman]Your right. 
optic did you just delete the contents of that drive? or did you install your own copy of xp?[/QUOTE]
Na, the computer came with XP on it. That drive was empty and I never noticed it lying there, it's just a secondary.

---

### Post by Optic on 2006-04-14
Thanks for the help guys, I'm going to try this out today.

---

### Post by spandon on 2006-04-14
Hi Optic,
Hopefully you read this prior to attempting an installation of ubuntu.
You didn´t specify what Acer model you have (mine is an Aspire 1654), so can only assume the system is recent and similar to mine.
1.  Before you do anything - BACKUP you present XP system by utilising the Acer bakup programme supplied (provided by Norton Ghost), to a dvd disk this will allow you to get your system back to it&#347; present condition if anything goes wrong.
2.  Test the machine out using a live cd (breezy 5.10 or Dapper flight 6 FIRST to see if it all works, before attempting to install.
3, If your hd is 100 gb (60/40 split) and you wish to leave C alone and use D for the installation, I would recomend you split D (30 as fat32 and 10 spare (E) for ubunto and swap -  the D can be used and seen by both  windows and Linux for data.
For both the live and install cd´s, I have to type in the following at boot :
Live cd
**live noapic nolapic, hd-detect/start_pcmcia=false, vga=771**
Install cd
[B]linux noapic nolapic, hd-detect/start_pcmcia=false, vga=771
[/B]
with these command lines my machine works perfectly for what I want it to do using ubuntu Breezy and Dapper.
Also do a search for acer laptops in general and your specific model in particular for the problems and workarounds particular to Acer machines.
Hope this helps
Enjoy
Don.

---

### Post by dabar12 on 2008-01-25
> **brainfry said:**
> My Acer laptop has a hidden partition at the start of the drive which enables diskless recovery of the XP system if something goes wrong. 
When I put Breezy on it, I went into disk management under XP, deleted drive D, rebooted and then partitoned the free space during the install.
Hope this helps.

how did you know the *hidden* partition was there?:confused: lol

---

