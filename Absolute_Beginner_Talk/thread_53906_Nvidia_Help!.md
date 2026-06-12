---
title: "Nvidia Help!"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-08-02
Post away as I may I'm not getting any definitive answers to my nvidia problems.

Why don't my color settings stick? I have to manually open nvidia-settings everytime I reboot to get my color adjustments to take effect. Why?

I have an Nvidia GeForce FX 5600XT 128 mb  4X card and I'm only getting 912 fps with glxgears. Why? Is that as good as this card gets? Should I get a new card for better performance?

What difference does hashing out "Load dri" make? Why is that important?

I'm using the synaptic nvidia-glx driver package...7174. Should I install the latest driver from Nvidia? Seems complicated for a Linux moron like myself, the readme weighs 10 LBs.! :) Also heard it had some problems. Is that true?

Really, really, appreciate some guidance here. Thanks!

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=grofaz]Post away as I may I'm not getting any definitive answers to my nvidia problems.

Why don't my color settings stick? I have to manually open nvidia-settings everytime I reboot to get my color adjustments to take effect. Why?
[/QUOTE]

Because the closed soruce Nvidia drivers don't work perfect with open source Gnome.

Its a little bother, but Linux Nvidia has a few things the Windows version lacks.

---

### Post by grofaz on 2005-08-02
Mmm...finally an answer...THANK you! :)

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=grofaz]Mmm...finally an answer...THANK you! :)[/QUOTE]

Sorry it took so long.

For example, the dual screen support for my 6600 GT in Linux BLOWS AWAY dual screen support in Windows. In Linux, I can have them be separate desktops (get this) at DIFFERENT RESOLUTIONS!

---

### Post by grofaz on 2005-08-02
Cool!

---

### Post by polo_step on 2005-08-03
[QUOTE=grofaz]
Why don't my color settings stick? I have to manually open nvidia-settings everytime I reboot to get my color adjustments to take effect. Why?[/quote]
I don't know as I haven't tried to adjust mine.

> I have an Nvidia GeForce FX 5600XT 128 mb  4X card and I'm only getting 912 fps with glxgears. Why? Is that as good as this card gets? Should I get a new card for better performance?
I recently got a BFG GeForce FX5500oc 128M (for $29.99 on sale) and it would not work in XP, despite a month's calling to their tech support, to the point of destroying the OS through incessant lockups and bluescreening.

I stuck it in the Linux box and it worked without much hassle.  I get around 1325 +/- in glxgears.  It is my understanding - gathered from posts here - that less than 1000 means that the advanced graphics aren't working. I don't know how to fix it, though, if they aren't.

> What difference does hashing out "Load dri" make? Why is that important?
I did this because someone told me that nVidia said to do it. I have no idea why you're supposed to do this, or even what DRI is or does.

> I'm using the synaptic nvidia-glx driver package...7174. Should I install the latest driver from Nvidia? 
I did, so maybe that's why mine works and yours doesn't, I dunno.

I obviously don't know much here, but I do know who the GroFAZ was. [-X

---

### Post by grofaz on 2005-08-03
The greatest leader of our day...cynically speaking of course. Good wargaming name though. :)

How did you install the current driver? Did you just run it or did you shut down the x server etc. as per the readme text? Bit daunting that!

"grofaz" OUT

---

### Post by polo_step on 2005-08-03
[QUOTE=grofaz]The greatest leader of our day...cynically speaking of course.[/quote]

Actually, it's a contraction of the German for "Greatest War Leader of All Time," a Goebbles quote.

> How did you install the current driver?
I have 7174 also, upon double-checking.  Apparently, I misremembered from the incessant driver un/re/installing/up/downgrading trauma in XP.

I installed according to [the last page of this thread.](http://ubuntuforums.org/showthread.php?t=43945) See where I came in...before that it's about UNinstalling the driver!

I did changes in xorg.conf and just rebooted.  I didn't screw around with shutting down X.  I don't leave my computer on because it's 107 here and I don't need the heat in the office. Note that this driver version does not recognize this specific card by name, but it works fine with it, and the card shows up as properly installed elsewhere.

There's [this page,](http://www.ubuntuforums.org/showpost.php?p=100460&postcount=1) but I haven't the courage to go through with it all.

---

### Post by grofaz on 2005-08-03
After my 4th pain in the ass (although much easier than Windows, I must say) reinstallation of ubuntu, I can say that if it ain't in synaptic (or apt-get) than FORGET IT!! I tried manually installing the latest nvidia driver set 76.67 and ended up with segmentation faults all over the place. So it's synaptic for me from now on !! And that's that for that.

Regards...

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=grofaz]After my 4th pain in the ass (although much easier than Windows, I must say) reinstallation of ubuntu, I can say that if it ain't in synaptic (or apt-get) than FORGET IT!! I tried manually installing the latest nvidia driver set 76.67 and ended up with segmentation faults all over the place. So it's synaptic for me from now on !! And that's that for that.

Regards...[/QUOTE]

Thats a very smart way to look at it.

---

### Post by grofaz on 2005-08-04
:)

---

### Post by codejunkie on 2005-08-04
[QUOTE=grofaz]
Why don't my color settings stick? I have to manually open nvidia-settings everytime I reboot to get my color adjustments to take effect.[/QUOTE]
you have to add ```
nvidia-settings -l
``` to Sessions in Gnome this will make it load your color settings at startup.

---

