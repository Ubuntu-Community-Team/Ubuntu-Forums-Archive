---
title: "Variety of probs - basics work but...."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by kornation on 2007-09-24
Gday!

Ok - variety of probs, but all, i beleive, linked, so please be paitient...

Ive got Ubuntu live cd and alt. disc...

The LIVE cd works well, installs, gets up and running (using now!), BUT only if my X550 grafics card isnt inserted. When the GFX card is slotted in it starts up, goes to loading screen then gets stuck (the loading bar gets stuck at around 20%ish).

Came here and found out about the x*** series of cards problem so...

The ALT. disc was downloaded and used to reinstall to fix this problem - but goes to a black screen on start (insted of the ubuntu loading screen), the pc 'sounds' like its still working (the usual hdd sounds etc). I tried using the recovery mode to do the 'fix' and it still doesn't work....

I also tried doing the 'fix' without the gfx card inserted while using the ALT, and with the LIVE cd version (without the GFX card inserted again).

So atm im currently back to using the 'live cd' version, no GFX card. I would like to have the GFX card working so i can try using Ubuntu for Second Life (I have an island there i currently cant get to...)

Specs....

P4 3.06Ghz (soc 524, 533mhz FSB, 1MB L2 Cache)
1x 1Gig ram + 256Mb ram stick
80Gig hdd (Seagate Barracuda 7200.9)
Tosh DVD +/- RW
Motherboard Intel® Desktop Board D101GGC ( V details found here V )
[http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/bdb/d101ggc/feature/index.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/desktop/bdb/d101ggc/feature/index.htm)

*** Sapphire Radeon X550 128mb VGA+DVI+TVO *** <- trying to put in

Currently running Ubuntu 7.04 (feisty fawn) installed off the live cd.

---Edit---

i checked this over a few times before posting to see if i had all info included but forgot to say please help and thank you if you do!

also, Bacon

---

### Post by bumanie on 2007-09-24
Not sure whether this will be helpful, but have you gone to the System --> Administration --> Restricted drivers. From there you should be able to load the ATI driver you are looking for. Failing this, there is a (I think) third party repository called envy, it apparently has the latest drivers from ATI and NVIDIA. Have never used this myself, but from what I have read, envy seems to solve people's hassles.

---

### Post by kornation on 2007-09-24
Hi - and thanks for the info - i tried Envy but it downloads and sets up the drivers for the current gfx card (ati radeon onboard 200 express), i cant get Ubuntu to load or even get to the recovery command line due to it crashing before it gets there when the gfx card is inserted.

i tried the 'fix' again but it got stuck again in the same place (the screen was just blank insted of seeing, well, anything after the 2/3 lines that pop up normally before the loading screen or lines of text.)

upon serching further afeild forums - i found around 3 more people asking the same question about the same type of card with no reply or 'gave up, used different card', yet the card is listed as 'supported' in all documentation found on ubuntu (after the fix) and on the ati radeon drivers list.

i would like to try and fix this, not just for myself,so there is a definitive way round for others with this popular cheap card, well partially for myself aswell because im missing second life and steam games atm.

I work across the road from a computer shop so could buy a new card, but the point of ubuntu is to make computing cheaper and easier, not to force into new hardware upgrades.

is there a way to manually setup a grafics card? when i set the mobo bios to use the onboard gfx card i could use '$ lspci' in the terminal to 'see' the card being read as a saphire x550 128meg, is there a way to use that info to manual insert the information needed to get this running?

Thanks again, and more bacon!

---

