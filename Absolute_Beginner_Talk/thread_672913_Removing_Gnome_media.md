---
title: "Removing Gnome media"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by chewit on 2008-01-20
Hi,

I want to remove Gnome Media, but it forces me to remove ubuntu-desktop. How do I just remove gnome media.

---

### Post by Malta paul on 2008-01-20
Hi, Go to System>Synaptic package manager, search for Gnome media, Right click and mark for for removal, apply.
Have fun:)

---

### Post by frup on 2008-01-20
Ubuntu desktop is a meta package. 

If you do remove Ubuntu desktop I believe the update process breaks or something.

---

### Post by chewit on 2008-01-20
Synaptic is where it forces me to uninstall ubuntu-desktop

---

### Post by Malta paul on 2008-01-20
frup is correct don't delete your desktop. I did it onceand then  hand had a problem for a while getting it back! Forgive me but why do you want to remove Gnome media?

---

### Post by chewit on 2008-01-20
> **Malta paul said:**
> frup is correct don't delete your desktop. I did it onceand then  hand had a problem for a while getting it back! Forgive me but why do you want to remove Gnome media?

I don't use any of the apps on Gnome media, I use VLC, totem & Rhythmbox

---

### Post by Malta paul on 2008-01-20
Thanks for your feedback. You know if it was me and your other players work OK, I'd just leave Gnome media on your system its not taking up much space. Better than screwing up  a good working system. 
Have fun :)

---

### Post by mcduck on 2008-01-20
Removing ubuntu-desktop does not remove your desktop.

It's just a metapackage, package that has no files but instead all the default programs included on Ubuntu's desktop listed as it's dependencies. So installing ubuntu-desktop will install all the default Ubuntu stuff.

Because no package depends on ubuntu-desktop, removing ubuntu-desktop doesn't remove anything else.

The only thing is that when you upgrade to the next Ubuntu version you should install the ubuntu-desktop package again to make sure that you'll get all new packages added to the new version.

---

