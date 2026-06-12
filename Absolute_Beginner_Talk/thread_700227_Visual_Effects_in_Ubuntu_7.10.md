---
title: "Visual Effects in Ubuntu 7.10"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by fatboysam on 2008-02-18
Hi,

Hoping someone can assist, I have a Apple MBP 17" C2D running VMWare Fusion 1.1.1 where I have set-up Ubuntu 7.10 but when I try to set the visual effects on (fyi, I have an nVidia GeForce 8600M GT and I have also run "Restricted Drivers Manager" and it came back saying "Your hardware does not need any retricted drivers"), I get the message:

Desktop effects could not be enabled.

Any ideas - really thought that my machine would be quite capable to run the visual effects.

Thanks.
fs.

---

### Post by aeiah on 2008-02-18
you're running vmware. your ubuntu installation is seeing vmware's virtual graphics card, not your nvidia card. vmware's graphics card wont have 3D open gl support in linux

---

### Post by merlinDwizzard on 2008-02-18
vmware (or vitrtualbox for that matter) does not support 3d graphics. Try running from the live disk (not install)and see if you can enable the advanced desktop effects from there. If so, you may consider dual booting.

---

### Post by aeiah on 2008-02-18
this page might be useful if you're thinking of installing and dualbooting ubuntu:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

you'll be able to use compiz / desktop effects etc. i dont think you'll be able to see them on the livecd as you'll need to download restricted drivers and i think it'll ask you to reboot (which of course will flush ubuntu out of your ram)

---

### Post by merlinDwizzard on 2008-02-18
you may be right, I'm taking for granted that i used remastersys to make a distro of my system after i had advanced desktop effects all set up as well as virtualbox installed. I wish there was a way i could share that out. Do anyone know how i could do that? It could be useful to someone having difficulties. It's larger than the 700mb initial install disc. It's around 2.5 gig and on a dvd of course. I'll check back here this evening when i get off work and look into that. If anyone has any suggestions i would be happy to provide that.

---

### Post by fatboysam on 2008-02-18
Thanks for the replies guys but I'm not going to bother with all the eye candy stuff if VMWare Fusion can't handle it - don't really have enough disk space to start installing different OS's via Bootcamp.

I must admit, it's really unfortunate that VMware Fusion can't handle it as under Setting=>Display it has a 3D accelerated grpahics option but seems to be for Windows XP SP2 VMs.

Thank again guys for ya help. I'll just stick with no Visual Effects.

see ya,
fs.

---

