---
title: "[SOLVED] Can a Previous Install affect desktop?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by YoYoSan on 2007-11-30
I've just repartioned my HD and done a fresh install of Ubuntu 7.10 from CD. 

On restart prompt after the install, my machine booted to the Gnome desktop with all hardware working (!) and I shut down for the night feeling rather smug (ha - that'll teach me!).

Today when I booted up everything ran fine through the normal Ubuntu (brown screen) log-in but the desktop is Xfce (without panels)

I'm running Xubuntu 7.04 on another partition and deliberately didn't import any docs or settings across when I installed Ubuntu 7.10.

Any ideas why this has happened and how I can get back (and keep) to Gnome on the new install?

I still want to keep my 7.04 Xubuntu install as a separate boot option until I've properly tested 7.10 i.e. checked all my hardware and got the wireless connections working.

Cheers

---

### Post by milton1 on 2007-11-30
I would start by making sure your grub entry for 7.10 is pointing to the correct partition. I have had multi-boot systems where update-grub gets the root partition wrong.

---

### Post by YoYoSan on 2007-11-30
Wouldn't that load the wrong partition?

The 7.10 partition is loading, and all apps are there - it's just running under Xfce

---

### Post by dondad on 2007-11-30
> **YoYoSan said:**
> I've just repartioned my HD and done a fresh install of Ubuntu 7.10 from CD. 

On restart prompt after the install, my machine booted to the Gnome desktop with all hardware working (!) and I shut down for the night feeling rather smug (ha - that'll teach me!).

Today when I booted up everything ran fine through the normal Ubuntu (brown screen) log-in but the desktop is Xfce (without panels)

I'm running Xubuntu 7.04 on another partition and deliberately didn't import any docs or settings across when I installed Ubuntu 7.10.

Any ideas why this has happened and how I can get back (and keep) to Gnome on the new install?

I still want to keep my 7.04 Xubuntu install as a separate boot option until I've properly tested 7.10 i.e. checked all my hardware and got the wireless connections working.

Cheers

Do you have a separate /home partition? If so, it will have the config files etc. from your previous install in hidden files. (unless you formatted it) If those files are there, that could explain why you see issues when you didn't import any settings.

---

### Post by YoYoSan on 2007-11-30
Yes I set up a home partition for 7.04 but I stuck everything for the 7.10 install onto a single partition - so I'm not (yet) accessing my old /home folder.

Hmmm.

---

### Post by YoYoSan on 2007-11-30
ah, sorry Milton1 - I hadn't realised that grub accessed other kernels on the hard drive - me being dumb.  Looking at the grub menu there's reference to the 7.04 install.

Time to have a poke around.

More hmmm

---

### Post by YoYoSan on 2007-11-30
From what I can see grub is accessing the correct partition to boot 7.10.

Having just checked with synaptic both Gnome & Xfce are loaded might - so maybe just remove Xfce?

---

### Post by YoYoSan on 2007-11-30
Sorted for now.

Using 'Options' at start up - apparently there was an X client script running - setting Gnome as default has sorted it.

I'd still like to know why on a clean install the desktop was switched on second, and subsequent boots.

But for now .. all well

Thanks for the responses.

---

