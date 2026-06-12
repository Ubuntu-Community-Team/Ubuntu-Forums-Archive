---
title: "G4 Imac will not boot Ubuntu Cd."
date: 2012-05-25
forum: Apple Hardware Users
---

### Post by Knightwise on 2012-05-25
Hey Guys, 

Bit of a mistery here. I just bought an older G4 Imac (17 inch model , 800 Mghz , 768 meg or ram ) and would love to run Linux on it. The problem is : it won't boot from Cd.

I get it to boot FROM the cd , but the setup won't start. When I boot with the C-key held down I get a brief flicker on the screen as it spins up the cd and then the screen goes blank.

When i boot up with the alt-key i get the 'boot from cd or hd' menu. I select the cd and the screen flickers .. and then the screen with the 'cd and hd' selection comes back but the colors are a little funky.

I've read somewhere it might be a graphics card issue ?  But i doubt that it would play an issue this early in the install.

Anyone have a clue ?

Tried :
Different cd's (burned at slowest possible speed)
Pram and NVram reset
Different distributions ( even debian ppc)
Alternate install Cd. 12.04 ppc

---

### Post by tabasko on 2012-05-25
Have you tried to boot Mac OSX install cd on that? It might be that cd-drive is not doing well so test booting from external drive.
Mechanical component like cd-drives might be already bit worn out on old machines like that.

I recommend xubuntu or lubuntu for that mac, unity even in 2D mode might not be very usable with those speeds.

I hope you get it running!

---

### Post by conal on 2012-05-25
Before Rsavage tells me off for dishing out bad advice (which I occasionally do!) have you read the PowerPC FAQ? [URL="https://wiki.ubuntu.com/PowerPCFAQ"]https://wiki.ubuntu.com/PowerPCFAQ
[/URL]

---

### Post by Knightwise on 2012-05-29
Good news !  I got it working.

What i did was (thanx to the help of the people in the #debianppc channel )

Boot in open firmware ( Command Option O F )
enter boot hd:,\install\yaboot

then the mac booted from cd rom ( Funny , because if you look at the open firmware manual one should type "enter boot cd:,\install\yaboot" to boot from cd. Turns out the terms for HD and CD are mixed up in open firmware.

I was now able to boot from the cd , using Yaboot.

---

