---
title: "Xfce w/ Ubuntu Studio?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ~Maxx on 2008-01-17
Hey everyone.  I *finally* got Studio on my main PC!  I ended up reinstalling Feisty, then upgrading to Gutsy, then upgrading to Studio - crazy!  Anyhow - I'm just sort of sitting here admiring it at the moment (hope I'm not the only one who did this :roll: ) - and I'm wondering a couple of things...  I currently have both Ubuntu and Xubuntu (Feisty) on my other (fairly old) pc, and I honestly prefer the Xubuntu desktop.  Aside from the difference in speed, I've grown rather accustomed to a few of the more minor cosmetic features that don't quite behave the same in Ubuntu.  So I'm wondering if it's possible to run Studio from the xfce desktop?  And, if so, would there be any benefit to this as far as overall performance of the audio apps (and the system as a whole) given my PCs specs?  I'd like to hear what people think on this matter, and if anyone out there has done it...

PC specs:  Gateway 2000, Pent. 4, 1500 Mhz, 768MB RAM, 100G/7200rpm hdd (<--Ubustu is the only thing on this drive - I dual boot w/ WinXP, but on a separate drive).

Looking forward to hearing opinions.  Thank you!

---

### Post by p_quarles on 2008-01-17
Yes. I haven't used Studio, but I'm fairly certain it's just a set of applications, along with the low-latency Linux kernel. The desktop environment you use isn't going to affect anything at the core of Ubuntu studio. 

So:
```
sudo apt-get install xubuntu-desktop
```
Log out, choose "options" in the login menu, go to "sessions," and select Xfce. Enjoy. 

Note, too, that this will not uninstall anything -- you'll still have the default desktop and everything that came with it, and you can choose that from your session menu at any time. Experimenting with this yourself is, in any case, worth the opinions of a hundred strangers on the internet. ;)

---

### Post by ~Maxx on 2008-01-17
> The desktop environment you use isn't going to affect anything at the core of Ubuntu studio.
So...  Don't be afraid to jump in with both feet, huh?  I actually did find (and subsequently loose) a post by someone who had installed the xfce desktop for UbuStu.  But there was no mention as to weather it improved performance.  I will install later this evening and post my results after a few days.

Thanks for the reply!

---

### Post by p_quarles on 2008-01-17
Xfce is getting heavier and heavier these days. You should still expect a bump in performance over Gnome or KDE on the same machine, but not a huge one. 

For what it's worth, I use the Fluxbox window manager (and my system's specs are slightly higher than yours). If you really want performance, there's no substitute for a lightweight desktop: Fluxbox, Openbox, PekWM, IceWM, and others. They're less user-friendly, but they'll run on boxes designed for Win98.

---

### Post by ~Maxx on 2008-01-18
> Xfce is getting heavier and heavier these days.
Figures.  I *just* started the upgrade from Feisty to Gutsy on my other pc.  

> You should still expect a bump in performance over Gnome or KDE on the same machine, but not a huge one.
Yeah.  The difference between the two on my other pc (Compaq Deskpro, Pent2, 256MB RAM) is minor, but noticeable.  Cosmetically there are just a couple of hardly-significant things about xfce that I prefer over gnome.  I'm glad I was able to play with both though and decide for myself.  

> I use the Fluxbox window manager (and my system's specs are slightly higher than yours).
I sampled MidiFlux and TinyFlux on my Compaq at first, but I'm still very new to Linux, and felt like I needed the security of the extra GUI bells and whistles. The worked very well though from what I could tell, and I see no reason why I might not reinstall one once I get a bit more comfortable with things.

Again - thanks so much for all your wisdom!  I'll post my progress when I have something to report (have to wait for this Xubuntu Gutsy upgrade to finish before I can install the xfce desktop to the UbuStu machine).  All the best!

---

### Post by urukrama on 2008-01-18
If you want a faster xfce, install xfce4 (sudo aptitude install xfce4) and not xubuntu-desktop. It gives you the xfce4 core, without all the extra applications that xubuntu-desktop comes with, and is faster in my experience.

---

