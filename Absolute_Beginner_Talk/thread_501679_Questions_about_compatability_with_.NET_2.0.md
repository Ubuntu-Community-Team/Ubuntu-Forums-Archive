---
title: "Questions about compatability with .NET 2.0?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by PrettyInUT on 2007-07-15
For my work, I have to use IE and have .NET 2.0 installed on my machine.

Can I do this in an emulator/similar program, or will I need to dual boot on my laptop to be able to log in to my work VPN software?

---

### Post by sparks0548 on 2007-07-15
I would say your best bet is to check out wine [www.winehq.com](www.winehq.com) or Cross Over Linux, [www.codeweavers.com](www.codeweavers.com).  You'll have to pay for Cross Over Linux, about $40 for the standard version.  I've used it and haven't had any problems with the application.  Dual booting is always an option if you have enough hard drive space or an additional drive to dual boot from.

---

### Post by rodo-&gt;dave on 2007-07-15
I have WinXP running in a VirtualBox VM and I can vpn to work through that... Also I have the .NET 2.0 installed and it seems to be working really well.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by MyR on 2007-07-15
.net does not work with wine or anything besides a vm or dual boot

---

### Post by rodo-&gt;dave on 2007-07-15
> **MyR said:**
> .net does not work with wine or anything besides a vm or dual boot

Actually, I am able to develop C# .NET apps on win32 that will run on linux using MONO.
I have a problem going from mono linux to win32 unless I use System.Windows.Forms (no linux gui creator yet).
But the monodevelop ide is pretty awesome and uses GTK with a gui builder similar to glade.

---

### Post by MyR on 2007-07-15
sorry, wherever i read that must be wrong. :/

---

### Post by rodo-&gt;dave on 2007-07-15
Well, I have to admit that most of my apps that I tested compat. mode have been fairly simple, as I tend to lean towards the linux ide anyway :)

---

### Post by PrettyInUT on 2007-07-15
Oooh, thanks, I'll try the VirtualBox!

I just like Ubuntu and didn't want to have to wrestle with using WinXP too (icky).

I'll let you guys know how it goes tomorrow :guitar:

---

### Post by PrettyInUT on 2007-07-18
I just wanted to report that after a few hiccups installing VirtualBox, it works swimmingly! I was able to log in to work just fine, And install games - hooray! Thanks so much. :KS

---

