---
title: "Installing Windows with Ubuntu"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Turrat on 2007-03-19
There are tons of how-to's on how to dual-boot Windows and Ubuntu. However, they say to install Windows first. My original Windows installation got corrupted over a year ago and I've been using Ubuntu ever since. But now that the university is offering tech students such as myself a free XP disk, I figured I might as well go for a dual-boot. Which brings me to my question; just what would I need to do to install Windows?

I know I'd need to create a partition at the beginning of the hard disk. But from there, do I just install Windows onto it and reinstall the grub? It seems too simple to be right, so I thought it better to ask first.

---

### Post by Zzl1xndd on 2007-03-19
Yep reinstall windows, it'll write over the MBR and you will need to reinstall and configure Grub but other then that it should be that easy.

---

### Post by charles.g.moore on 2007-03-19
> **Turrat said:**
> There are tons of how-to's on how to dual-boot Windows and Ubuntu. However, they say to install Windows first. My original Windows installation got corrupted over a year ago and I've been using Ubuntu ever since. But now that the university is offering tech students such as myself a free XP disk, I figured I might as well go for a dual-boot. Which brings me to my question; just what would I need to do to install Windows?

I know I'd need to create a partition at the beginning of the hard disk. But from there, do I just install Windows onto it and reinstall the grub? It seems too simple to be right, so I thought it better to ask first.

If you are not going to do any hardcore gaming and just want to run a few windows apps you should think about installing windows in a virtual machine environment.
Check out VMWare, there are other virtualization programs that I heard were better.  I use VMWare and it does all I need it to...

If you use XP in VMWare you can just fire it u in your ubuntu whenever you need it then shut it down

---

### Post by kpkeerthi on 2007-03-19
> **Turrat said:**
> There are tons of how-to's on how to dual-boot Windows and Ubuntu. However, they say to install Windows first. My original Windows installation got corrupted over a year ago and I've been using Ubuntu ever since. But now that the university is offering tech students such as myself a free XP disk, I figured I might as well go for a dual-boot. Which brings me to my question; just what would I need to do to install Windows?

I know I'd need to create a partition at the beginning of the hard disk. But from there, do I just install Windows onto it and reinstall the grub? It seems too simple to be right, so I thought it better to ask first.

Yep and you should be OK. Follow [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113) on how to get your GRUB back.

---

### Post by zvacet on 2007-03-19
[http://ubuntuforums.org/showthread.php?t=358183&highlight=install+windows]("http://ubuntuforums.org/showthread.php?t=358183&highlight=install+windows")

---

