---
title: "Linux beginner (so be nice)"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by FalconSR on 2006-08-11
hey guys and gals (if any),
im new to linux so be nice

i installed SuSE 10.1 the other day but was sick of the grub boot loader (im very fussy) anyways formatted whole computer cause i couldnt find that ***** file

now i got Ubuntu install CD's from uni and gave that a shot and i like what i see... still has grub though

anyways my problem is (both SuSE and Ubuntu) is that i cant access/see/find my SATA and PATA HDD's..SuSE let me see other PATA, Ubuntu wont let me see any other.. also im not sure if drivers are installed properly..:confused: 

my specs are 
Asus A8N ALI SE
1gig Dual Channel kingmax/kingston hardcore ram
3200+ AMD 64bit
1x 20gig PATA      linux installed
1x 120gig PATA     partitioned with win XP pro on
1x 250gig SATA     other files ie games, setup files
1x 80gig SATA      music
1x Floppy << if that helps yes i still have one

I dont no much code besides rm, cd, etc so please explain in full detail.
also im new to these forums and OS but is it possible to run *windows* games which are already installed straight on linux? or do i have to install it on linux to play?

thanks heaps

---

### Post by kaffelars on 2006-08-11
Sorry, but I do not know anything related to your disk problems :sad: 

Regarding your games problems, you can not run games that are installed in Windows. By this I mean that you have to install them in Linux. To run Windows games in Linux, there are a couple of alternatives:

The easiest (at least if you have an Nvidia graphics card) is to get Cedega (read more [here]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&file=index&ceid=29")). Cedega is a polished and modified version of Wine, made for games. 
It's not free (of charge) but it's not expensive either, and it works pretty well as far as I know. :) 

Another alternative is to install the games with the Loki Installers for Linux games (see [here]("http://liflg.org/")). 

Yet another alternative is simply to use [Wine]("http://www.winehq.org"). 

Good luck :)

---

### Post by FalconSR on 2006-08-11
yeah ill leave that till later on... no chance anyone else knows how to get my HDD's showing up and accessable

also another prob i can share a folder but when windows computer tries opening it comes up with password prompt and they type my root and username passwords and nothing works...any ideas

also sorta need my printer canon IP1000 i downloaded the so called linux drivers and it says it couldnt open the file... they are .rpm files what installs them?

im starting to HATE linux every minute i use it

---

### Post by Tomosaur on 2006-08-11
Your hard disk problems may just be the result of you not knowing _where_ they're located.

Please open a terminal, and type the following command:
```

cat /etc/fstab

```

This will dump the contents of the 'fstab' file (which is found in the /etc/ directory, into the terminal. Copy and paste it up here please.

---

