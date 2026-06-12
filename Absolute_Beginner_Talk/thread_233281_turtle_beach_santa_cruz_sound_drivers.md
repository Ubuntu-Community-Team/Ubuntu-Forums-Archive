---
title: "turtle beach santa cruz sound drivers??"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by 8nout on 2006-08-09
Hello all, installed Frostwire, dl'd some mp3's but have no sound. I have googled for help but most findings were very complicated for me. How can I check to see if my TB sound card is even recognized? Also, can play cd's, you know...the slider moves across the bar, but no sound.

Thanks...

---

### Post by GuitarHero on 2006-08-09
Did you install multimedia codecs?  ubuntu does not play mp3's out of the box.  The easiest way to get them is use the programs easy ubuntu or automatix to do it for you.  Theres also a page in the wiki called restricted formats that tells you how to do it yourself.

---

### Post by 8nout on 2006-08-09
Thanks for quick reply... I installed multimedia codecs with automtix...

How do I find the wiki page?

---

### Post by GuitarHero on 2006-08-09
Ok go to System>Administration>Device Manager
Everything is listed htere, look to se if your card is recognized.

---

### Post by 8nout on 2006-08-09
OOPS< I don't see the sound card...it looks as though it only sees the on-board sound....

---

### Post by GuitarHero on 2006-08-09
Yep you dont have drivers for it installed.  Look on the manufacturers website for linux drivers.  Chance are they wont have any, in that case look up the chipset of the sound card and maybe we can find drivers for the chipset.

---

### Post by 8nout on 2006-08-09
Thanks!! I will do my best...

---

### Post by 8nout on 2006-08-09
chipset is crystal CS4630...

---

### Post by GuitarHero on 2006-08-09
Well its not listed on
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
So we dont know either way if it will work or not.  Im searching for drivers now...
This looks like it might be what you need:
[http://www.opendrivers.com/driver/217908/crystal-cs4614-cs4624-cs4630-cs4280-sound-driver-windows-98se-me-2000-free-download.html](http://www.opendrivers.com/driver/217908/crystal-cs4614-cs4624-cs4630-cs4280-sound-driver-windows-98se-me-2000-free-download.html)

---

### Post by 8nout on 2006-08-09
dl'd file and opened but the .exe file will not run....? maybe not a linux file.? I see in the wiki link that a Hercules Fortissimo card has a CS46XX chipset that will run with simple mods...using SPDIF. might there be help there?

I have a dual boot setup with XP, if all else fails,, can I run on-board sound with ubuntu and TB card with XP?

Thanks for your time and help but gotta go to bed..will be back tomorrow....God willing...

---

### Post by Linux4HumanBeings on 2006-08-10
I have the same problem! I dono how to fix it I have no sound

---

### Post by 8nout on 2006-08-10
Hi Again, how can I get my on-board sound to work?

---

### Post by jeffathehutt on 2006-08-10
I think the problem lies from the two conflicting sound cards.  I have a Santa Cruz on my computer, and it works fine right out of the box.  All you have to do to make it work is to disable the onboard sound card from your bios setup screen.  If you have your speakers connected to the Santa Cruz there shouldn't be any problem disabling the onboard one, since Windows will also be using the Santa Cruz.

---

### Post by 8nout on 2006-08-10
Thanks for the reply!! I think I already have the on-board sound disabled but will check again...Glad to hear a Santa cruz will work!

---

### Post by tudsy on 2006-08-20
> **jeffathehutt said:**
> I have a Santa Cruz on my computer, and it works fine right out of the box.  

Can you check to see what driver you have running?  I've tried everything and cannot get a single peep out of my Santa Cruz (onboard sound is disabled, so that's not it).  I have problems loading the snd-cs46xx drivers, it just won't do it.

Thanks!

---

