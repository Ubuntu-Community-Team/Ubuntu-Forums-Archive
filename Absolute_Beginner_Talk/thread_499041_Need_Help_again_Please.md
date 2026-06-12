---
title: "Need Help again Please"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-07-12
I recently did some upgrade work on my PC and in the process changed my drives around, but seem to have found a little problem that I hope you can help me with.

I recently backed up my data on Ubuntu to disk and because it was on my 100gig HDD decided to move it over to my 10gigHDD, and wipe my 100gig HDD and repatition it and put windows on a patition on the 100gig hdd, (Clare as mud so far right).

well I deleted all the ubuntu stuff off the 100gigdrive (formaly the home drive for Ubuntu) and then successfully patationed the drive and ghosted all the windows files over to the new patition. so far so good then I changed the designation of the drive (100gig HDD) to master not slave, and made sure that I could boot from this drive, ALL good sofar.

next I wiped the 10gig hdd and proceded to install Ubuntu on that drive.

to ensure that I did not install ubuntu on to any of the nwe pations I disconected the 100gig driveso that it would only install on the 10gig drive, all seemed to go well and like clockwork untill I reconected the 100gig drive, and rebooted. and guess what? it booted stright into windows XP.

What happened to the screen that ask's what drive you want to boot from? and how do I get it back?

---

### Post by drowner on 2007-07-12
What's happened here is GRUB (the program that lets you choose) has been installed to the 10gb drive, right, but your computer isnt looking at the 10gb drive at boot, it looks at the master, which contains only windows data. Clear as mud? heh heh.

I've never had this problem before, but I think a little program called the SuperGrubDisc can help you, i'll let someone else with more experience sort it out.

It should be fine, you just need to install GRUB to the 100gig hard drive.

---

### Post by Big_Kiwi on 2007-07-12
I have recently Aquired a progam called hard disk manager 8.0, dose any one know this progam? and if so gan I use it to sett uo a duel boot system on windows xp startup

---

### Post by robertc36 on 2007-07-12
I guess thats paragon.
You need a boot manager .So i would google that.

---

### Post by Big_Kiwi on 2007-07-12
thats Great and I would do that how??? LOL

---

### Post by robertc36 on 2007-07-12
Dont!!!
Some would need that explaining lol!
I think  disk director has one included .

---

### Post by Big_Kiwi on 2007-07-12
just going slightly off topic dose any one know why google search has somany ????? all over it hard to under stand any results seems like it has been censored

---

### Post by robertc36 on 2007-07-12
It is ok for me seems you might have another prob to look into later lol
I have never heard of this; best guess fonts.

---

