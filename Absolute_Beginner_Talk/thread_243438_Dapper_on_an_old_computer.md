---
title: "Dapper on an old computer?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-25
I have successfully installed Hoary and XP to dual boot on my antiquated computer:

AMD 450mhz
128 MB ram
8G HD (yes, I was able to squeeze both OSes in :p )

I've been using Hoary for quite awhile now ...oh, around ... 3 DAYS! :mrgreen: Mostly figuring things out.  Then, I just got hold of Ubuntu Dapper and Kubuntu, yesterday.  I installed Ubuntu successfully, however, once I installed it, it was too slow.  I guess my computer couldn't take it.  The programs were slow, and my computer makes a weird clicking sound at regular intervals.  It appears that my HD writes occassionally. I guess my memory is too small so it writes to the HD to compensate.

Anyway, I re-installed Hoary and I'm ok. I'm wondering, however, if maybe I could still make Dapper work on my computer without slowing it down?  I'm thinking maybe there are some things I could adjust with the settings to make Dapper less ... resource intensive.  I'm assuming that's why it's slow on my computer. 

Any suggestions?

Also, I was hoping I could update hoary's GIMP version with Dapper's, but I don't know where the GIMP installer file is on the Dapper CD, and how I can install it.

Help? :(

---

### Post by Jerome36 on 2006-08-25
You might want to try Xubuntu.  It's basically just like Ubuntu, but instead of using the Gnome desktop enviornment, it uses Xcfe.  Xcfe is great for older machines because it doesn't demand as much system resources and is lighter then Gnome or KDE (KDE is the enviornment for Kubuntu).

I built a new computer last fall, which runs Windows XP, but I decided to put Ubuntu on the old computer (removing Windows from that one completely).  It's a 350 mhz Pentium 2, with 192 mb of RAM.  Unfortunetly the hard drive swaps quite often, which is what is happening with you, because you don't have enough system memory.  I'd suggest installing the Xcfe destkop enviornment, and/or adding more RAM.  I'm planning on doubling the RAM in my old computer (it's max is 384, or whatever), and putting in a faster Pentium 2 (cheap on eBay).

Anyway, the nice thing is you can still install Ubuntu, and then add Xcfe once the install is complete.  Then, when you boot the machine, and you select Linux, you can pick which desktop enviornment to use.

---

### Post by Druidor on 2006-08-25
I am currently running Dapper on a PIII 450MHz machine wiht 256Mb of memory, 40Gb HD & yes the programs can take a short while to open, their is no real lag once they are up & running.

---

### Post by ahaslam on 2006-08-25
Personally I'd install Xubuntu & download kdebase for a light KDE session as well as Xfce.

Then I'd download preload & BUM (boot up manager) from the repo's.
Using preload may slow the boot of your machine, but shout enable apps to load faster.
Using BUM will allow you to select what starts during boot. 
I found a good service to start was hdparm, this tweaks your hard drive settings.


Tony.

---

### Post by bombitmd on 2006-08-25
ok, I guess I'll try Kubuntu.  Otherwise, I'll stick with Hoary for now.  Besides,  I'm still learning how to maximize the use of Linux, so by the time I can upgrade my computer and install a newer version of Linux, I should be quite familiar with Linux already.  Thanks!

---

### Post by ahaslam on 2006-08-25
> **bombitmd said:**
> ok, I guess I'll try Kubuntu.  Otherwise, I'll stick with Hoary for now.  Besides,  I'm still learning how to maximize the use of Linux, so by the time I can upgrade my computer and install a newer version of Linux, I should be quite familiar with Linux already.  Thanks!
Kubuntu ?

---

### Post by Jerome36 on 2006-08-25
> **bombitmd said:**
> ok, I guess I'll try Kubuntu.  Otherwise, I'll stick with Hoary for now.  Besides,  I'm still learning how to maximize the use of Linux, so by the time I can upgrade my computer and install a newer version of Linux, I should be quite familiar with Linux already.  Thanks!

I'm sure that was a typo.  Did you mean **X**ubuntu?  Kubuntu will probably run even slower then Ubuntu on that computer.  I could be wrong, but I've heard most people say KDE is a little more demanding then Gnome.  I haven't used KDE in years though.

---

