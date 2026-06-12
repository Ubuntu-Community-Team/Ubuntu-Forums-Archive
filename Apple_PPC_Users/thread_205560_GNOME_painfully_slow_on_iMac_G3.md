---
title: "GNOME painfully slow on iMac G3"
date: 2006-06-28
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-06-28
Can any G3 users help me with this? 

I have a lime green iMac with 6.4 GB of hard drive space and 6.06 LTS installed. . .I don't know what to say except that it has become so slow I can't even access Firefox without a two minute wait - if I'm lucky.

I tried doing everything I could on 5.10 to make it faster in certain areas. . .getting rid of panels, applets, switching to a GTK greeter with simple black desktop.  None of that worked.  

I think the processor on this machine is somewhere around 400 MHz, and its currently running the 2.6.15.25 kernel.

Are there any window managers I could switch to in order to be able to use it without pulling my hair out?

---

### Post by Ptero-4 on 2006-06-28
Xfce or fluxbox.

---

### Post by RavenOfOdin on 2006-06-28
Okay, I'll look into those.
Thanks.

I'm running Enlightenment E16 atm and its giving me much better performance, but window shading and theme configs seem to get mangled every so often.

---

### Post by RHTopics on 2006-06-28
How much memory do you have installed?

The more memory you have, the better your performance will be.

---

### Post by anurse on 2006-06-28
Firefox, slows things down on my machine (a slot loading G3). Unless you need the features it offers,  you might consider using KDE and Konqueror as your web browser. Its fine if you're checking the scores, using a light weight web mail, looking up references, etc. In addition, I found KDE office apps simply more responsive than gnome, perhaps because of better integration?

---

### Post by emf on 2006-06-28
I use a G3 with fluxbox 0.9.15.1 and 128MB RAM.  I think fluxbox works great.  If you are new to fluxbox and you want to look at my config files (startup, menu, init, keys, groups), let me know.  I'm sure you could find better files if you looked around, but if you're feeling lazy I don't mind sharing.  They'd be pretty easy to manipulate to your own liking.

As for Firefox with a G3 and not much RAM, don't bother.  Firefox is slow to startup no matter what you do.  Extensions are cool, but they're not worth the sacrifice in speed.  Opera works much better for me.  I even like to use Dillo when I can.

anyway, good luck.

---

### Post by Sav on 2006-06-29
Try Xubuntu.
It runs almost smooth on my iMac g3 with 256 mb ram.

---

### Post by nkbj on 2006-06-29
Try commenting out (by placing a # at the beginning of the line) this line in /etc/X11/xorg.conf:```
Load    "dri"
```

---

### Post by AirRaven on 2006-06-29
You could try Epiphany (epiphany-browser in the repos). I find that's a lot faster to load than Firefox.

---

### Post by DJ_Max on 2006-06-29
His problem is not with Firefox, but with Gnome. Try *nkbj* solution. I have an iMac G3 400MHZ with 256MB of ram and a 40GB HD, and it runs just fine, I even used KDE at one time. Maybe it's a hardware issue.

---

### Post by RavenOfOdin on 2006-06-29
[QUOTE=RHTopics]How much memory do you have installed?

The more memory you have, the better your performance will be.[/QUOTE]

[http://www.everymac.com/systems/apple/imac/stats/imac_333.html](http://www.everymac.com/systems/apple/imac/stats/imac_333.html)

---

### Post by emf on 2006-06-29
Definitely try nkbj's suggestion first, but I still think you'll benefit from a slimmed-down window manager.  I have both Gnome and fluxbox installed on my G3, and while i really like Gnome, it doesn't really compare in speed on an older computer.

I'm not sure just how much ram you have (the standard '333' has just 32MB!), and I don't know of any real minimum system requirements for ubuntu, but you have an old enough system that I would think removing Gnome and giving xubuntu, fluxbox, or iceWM, etc., a try would lead to a much better experience.  It'll be faster and you'll have more space available for programs and personal files.  Not to mention the smaller WM or DE can get pretty addictive.

---

### Post by DJ_Max on 2006-06-30
[QUOTE=RavenOfOdin][http://www.everymac.com/systems/apple/imac/stats/imac_333.html](http://www.everymac.com/systems/apple/imac/stats/imac_333.html)[/QUOTE]
That's your problem right there, you need more RAM. You really can't run a desktop environment with only 32MB of RAM. Maybe Fluxbox, but I'm not sure, because Xorg  will use a lot of RAM.

---

### Post by RavenOfOdin on 2006-06-30
[QUOTE=DJ_Max]That's your problem right there, you need more RAM. You really can't run a desktop environment with only 32MB of RAM. Maybe Fluxbox, but I'm not sure, because Xorg  will use a lot of RAM.[/QUOTE]

I don't have problems with either E16 or XFCE, the latter not unless I enable GNOME integration. Then it starts slowing down just a little. But I think I can live without that.

---

### Post by RHTopics on 2006-06-30
RavenOfOdin,

Would you run the "top" command from a terminal window and then report back the memory usage it shows?

You must be using your swap partition quite extensively if you have just 32mb of ram.

---

### Post by RavenOfOdin on 2006-06-30
[QUOTE=RHTopics]RavenOfOdin,

Would you run the "top" command from a terminal window and then report back the memory usage it shows?

You must be using your swap partition quite extensively if you have just 32mb of ram.[/QUOTE]

load average: 0.43, 0.46, 0.42 Tasks 55 total, 1 running, 54 sleeping, 0 stopped, 0 zombie. Cpu(s): 17.7% us, 3.3% sy, 0.0% ni, 75.5%id, 0.0%wa, 0.0% hi, 0.0% si
Mem: 61360k total, 60476k used, 860k free, 1248k buffers
Swap: 249992k total, 81364k used, 168628k free, 19600k cached

---

### Post by RHTopics on 2006-06-30
RavenOfOdin,

Thanks.  Well, you have more than 32MB of RAM (64 MB?), and your swap partition is being used (80 MB).

By adding or replacing RAM with larger size RAM chips, you will definitely see a huge improvement in performance.

I believe with your model iMac, you can safely increase your memory to 384MB.  That is, with one 256MB chip in the larger memory slot and a 128MB chip in the smaller slot.  Crucial Memory lists the price for the 256MB chip ( CT484868 ) at $46.55 and the 128MB chip ( CT136249 ) for $44.61.

I have a slot-loading iMac G3 350mhz with 384MB running a standard Ubuntu 5.10 setup.  The swap partition is seldom used.

Adding memory to your iMac is not as simple compared to the slot-loading iMac, but it is worth the time and money if you want to see a major improvement in speed.

---

