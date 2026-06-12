---
title: "help! wireless doesn't work anymore."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by false_cognate on 2007-04-19
Since I've installed Feisty, my wireless has been broken. At first, it wouldn't even show nearby networks, but now it shows networks but will not connect.

I've got a Broadcom 4306 according to hardware info.
I've downloaded the .deb of Broadcom drivers from the relevant topic and installed (that is when it started detecting networks).
I removed ndiswrapper (I was using it under Edgy and it worked, however something changed in Feisty and I couldn't get it to work so I removed it in case it conflicted).
I also removed network-manager (didn't seem to help).
I installed Wicd (which shows the networks, but hangs upon connecting and won't connect, except for a wired connection).

---

### Post by rich.bradshaw on 2007-04-20
on mine I blacklisted the broadcom driver, then used ndiswrapper for a similar card. Try searching around for your particular card. I wouldn't get rid of network manager - that was how I got mine to work!

---

### Post by teddybairs1 on 2007-04-20
Broadcom drivers can be tricky, and sometimes don't seem to have any rhyme or reason as to why they work or don't work. I've got a Broadcom 4318, what some would call the "accursed" wifi card. It worked with ndiswrapper under edgy. When I installed fiesty the first time, it worked with ndiswrapper, and then X crashed on me and I had to reinstall it (I was running the beta). When I went to use ndiswrapper again, it didn't want to work. I fiddled with it, and decided to reset it to the default bcm43xx driver with the firmware (someone packaged a nice .deb here on the site, try searching for it), and lo and behold it decided to work when it never did before! That's what I'm using right now to connect to our router as I write this.

Give the bcm43xx a try with the firmware. To do so, you need to uninstall ndiswrapper. put network-manager back on the system. It's there for a reason.

---

