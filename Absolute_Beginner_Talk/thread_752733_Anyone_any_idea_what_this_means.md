---
title: "Anyone any idea what this means?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Zralou on 2008-04-11
I clicked on the update icon tonight to download the lastest updates (Hardy Heron).  After downloading all the updates, Apt started to install, but stopped with the message:

Sara Lou

---

### Post by Zralou on 2008-04-11
After searching through the downloads I found this too?

Sara Lou

---

### Post by Jon Monreal on 2008-04-11
> **Zralou said:**
> I clicked on the update icon tonight to download the lastest updates (Hardy Heron).  After downloading all the updates, Apt started to install, but stopped with the message:

Sara Lou
Did the Hardy Heron install get interrupted? Perhaps the installation did not complete correctly. You could try installing the packages from the Hardy Heron CD/DVD if you have one or going through the update process again for those packages.

I had this happen with a Ubuntu installation a while back (not Hardy Heron) and it produced similar results.

Hope this helps.

---

### Post by zvacet on 2008-04-12
```
sudo apt-get -f install
```

---

### Post by Zralou on 2008-04-12
> **Jon Monreal said:**
> Did the Hardy Heron install get interrupted? Perhaps the installation did not complete correctly. You could try installing the packages from the Hardy Heron CD/DVD if you have one or going through the update process again for those packages.

I had this happen with a Ubuntu installation a while back (not Hardy Heron) and it produced similar results.

Hope this helps.

Hardy has been running fine for 2-3 weeks now, this was just the regular update process.  I don't know if its related or not, but something broke my Nvidia drivers again at the same time.  Just before I logged in and started the updates, I had to start up with vesa drivers because I couldn't get X to start.

Sara Lou

---

### Post by Zralou on 2008-04-12
> **zvacet said:**
> ```
sudo apt-get -f install
```

What does that do?.  I like to learn as I go, instead of just copying code, that way, hopefully I can fix it myself the next time it breaks..

Sara Lou

---

### Post by otrojake on 2008-04-12
The -f flag for apt-get attempts to fix broken packages and dependencies.

---

### Post by Zralou on 2008-04-12
Ahh ok, thanks.  I'll give it a try now.

Sara Lou

---

### Post by JoshuaRL on 2008-04-12
You also might try:
```

sudo dpkg --configure -a

```
It will fix any broken packages through dpkg.

Another idea is to go to Synaptic Package Manager, look at the bottom under Custom Filters, and look at the Broken packages filter.  If you see anything in there, have Synaptic reinstall.

---

### Post by Zralou on 2008-04-12
> **zvacet said:**
> ```
sudo apt-get -f install
```

Ran the code, re-started the update process, everything works great.  Big thank you zvacet.:KS

Sara Lou

---

