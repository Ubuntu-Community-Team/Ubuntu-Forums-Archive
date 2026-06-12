---
title: "Asus T91MT Screen Error"
date: 2012-05-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by quadbikeben on 2012-05-30
Hi Guys!

I Have a little Asus T91MT running Ubuntu 12.04 and it has a screen error that makes the screen half itself but when i log out it is all normal and fine the whole screen is being used but when i log in it freezes the bottom half and the top half is trying to fit the whole screen into it but is very pixely if you know what i mean and just very hard to use.

i have re-installed it a few time but it just keeps coming back to me and when it boots it is using the whole screen but the second it logs in it half's again.

My Device Has :
A AsusTeK T91MT Asus Mother Board
2 gig of ram
31 gig ssd
intel atom
most likely has a intel graphics card built in to the motherboard

and i DON'T know of any driver installed that is running the screen
but sometimes it boots normally and the screen it fine.

Any way I Really Need Some Help!

---

### Post by 2F4U on 2012-05-30
You should probably add the hardware specs of your machine. Don't forget to add the graphics card and what graphics driver you are currently using.

---

### Post by quadbikeben on 2012-05-30
Specs are up but not sure on the graphics card i think its a intel one

---

### Post by 2F4U on 2012-05-30
There is a good tutorial here in the forum:

[http://ubuntuforums.org/showthread.php?t=1919147](http://ubuntuforums.org/showthread.php?t=1919147)

It seems as if you need a special graphics driver for your card.

---

### Post by JorgeGhersa on 2012-06-18
There's no need for a "special" driver for the t91mt, just adding some options to the grub configuration so it blocks a "bad" driver it defaults to, and uses the good (good enough, as it is still being perfected) one.

To get it working follow the steps written [here]("http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/"). More info [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") and in the [mega-thread for the card]("http://ubuntuforums.org/showthread.php?t=1229345") (now closed to follow on a new one).

Good luck.

---

### Post by jobani on 2012-07-31
Use ubuntu 11.04. There's a known display driver issue on eeePC using 12.04.

---

