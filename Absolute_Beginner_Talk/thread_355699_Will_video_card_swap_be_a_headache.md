---
title: "Will video card swap be a headache?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by bullpen7979 on 2007-02-07
Looking to beef up the graphics card in my existing machine (Kubuntu Edgy) How to proceed? Just pop it in and reboot? Will Kubuntu find the drivers, or will this be a major operation. Switching to Rage Ultra 2000 xp card to try to gain some better display resolution and refresh rates....

Thanks list...

---

### Post by Sunflower1970 on 2007-02-07
Are you switch out an nVidia card for the ATI card? 

If it's an nVidia for an nVidia, I don't think there's a problem. I did it, and everything went fine. Don't know if it's an ATI card for an ATI card, I'd expect there'd be no problem.

I also switched out an ATI card for an nVidia card in another computer, and I had trouble there....ended up having to reinstall everything...(I think moreso because I did something idiotic, but for the life of me I don't know what I did....)

---

### Post by mcduck on 2007-02-07
Switching cards shouldn't be any problem, as long as you make sure that when you power the machine off last time you configure your xorg.conf to use some graphics driver that works on your new card. 'vesa' would be a good option when switching between cards from different manufacturers.

---

### Post by dpmccoy on 2007-02-07
I swapped out my ATI Radeon 9550 last week for a new Nvidia Ge Force 7600.

It was a lot easier than I expected.

To be perfectly safe, I ran "dpkg-reconfigure xserver-xorg" and reset my video card type to "vesa".  I turned it off, replaced the card, and rebooted.  Once I did that, I installed the new Nvidia beta drivers through the instructions on one of the forum posts.  I restarted the xserver, and everything has been working beautifully since.

---

