---
title: "Burn Data to DVD"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by SniperClops on 2008-02-28
Greetings,

What program do I have to install to burn data to a DVD?

Thanks

---

### Post by wolfen69 on 2008-02-28
you could use K3B, Gnomebaker, or Brasero to name a few. K3B is the best in my opinion.

---

### Post by imT on 2008-02-28
is preinstalled, just pop-in a dvd and burn it :)

---

### Post by Duck2006 on 2008-02-28
You can try K3b. You can get it from Add/Remove.

---

### Post by ajgreeny on 2008-02-28
+1 for k3b, the best CD/DVD burner software for any platform, in my opinion.  Brasero is getting better and very close, but still not quite up to k3b as far as I can see.

---

### Post by SniperClops on 2008-02-28
I just tried what imT said and it worked. I had a file larger than 2 GB and Nero Express said it couldn't burn something that large on DVD. 

Thanks for all your suggestions.

GO LINUX!

---

### Post by Oldsoldier2003 on 2008-02-28
> **wolfen69 said:**
> you could use K3B, Gnomebaker, or Brasero to name a few. K3B is the best in my opinion.
K3b works better for multisession cds thats a fact. thats why even gnomies seem to prefer it...

---

### Post by Northsider on 2008-02-28
K3B worked perfectly for my dvd burns, but can it *copy * dvds as well?

---

### Post by TeoBigusGeekus on 2008-02-28
Had some issues with K3B - it wouldn't exit after burn.
I've been using Brasero ever since (to get in sync with Hardy Heron :)) without any problems.

---

### Post by stchman on 2008-02-28
> **SniperClops said:**
> Greetings,

What program do I have to install to burn data to a DVD?

Thanks

Yes, K3B is the best CD/DVD burning application for Linux period.

To install do the following in a terminal:

```
sudo apt-get -y install k3b libk3b2-mp3
```

This will install K3B and the mp3 plugin.

If you are running Gnome do the following to load the KDE libraries at start up.  This will speed up the loading process of KDE apps under Gnome.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

---

### Post by stchman on 2008-02-28
> **Northsider said:**
> K3B worked perfectly for my dvd burns, but can it *copy * dvds as well?

Yes, K3b will copy UN-ENCRYPTED DVDs no problem.  Encrypted DVDs will need to use K9Copy or DVDShrink.

---

