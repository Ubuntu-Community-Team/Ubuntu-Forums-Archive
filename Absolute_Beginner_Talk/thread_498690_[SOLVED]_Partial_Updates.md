---
title: "[SOLVED] Partial Updates"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-07-11
I keep getting this partial upgrade message on every update installation. When I click the partial update, it asks me whether i want to install the whole ubuntu-desktop including all other software (I had removed it while removing evolution and a bunch of other software i wasnt using).

The packages compiz-core , compiz-gnome and compiz-plugins are greyed out and i cannot select them. They remain greyed even after I install the other packages. Please see the 3 screenshots.


What could be the problem ?

---

### Post by solar george on 2007-07-11
It is possible that your beryl install is conflicting with compiz

---

### Post by Inxsible on 2007-07-11
But this just started happening in the last week or so....I installed Beryl about 6 months back

---

### Post by zvacet on 2007-07-12
> When I click the partial update, it asks me whether i want to install the whole ubuntu-desktop

So,say yes.Ubuntu-desktop is meta-package and you can remove it with no problem,but you need it if you want to do upgrade.

---

### Post by sailor2001 on 2007-07-12
I interpret it to mean that compiz is unsupported in that download group so has to be upgraded separately

---

### Post by mcduck on 2007-07-12
> **Inxsible said:**
> I keep getting this partial upgrade message on every update installation. When I click the partial update, it asks me whether i want to install the whole ubuntu-desktop including all other software (I had removed it while removing evolution and a bunch of other software i wasnt using).

The packages compiz-core , compiz-gnome and compiz-plugins are greyed out and i cannot select them. They remain greyed even after I install the other packages. Please see the 3 screenshots.


What could be the problem ?

Probably the Compiz update needs to either remove some package that used to be part of Compiz but is not needed any more, or then it may need to install some new package that has been added to Compiz. The update manager doesn't allow removing or adding new packages, only updating the existing ones, so you need to use Synaptic to do the upgrade. Browse to upgradeable packages with Synaptic and select all & mark for upgrade. Most likely that solves your problem, and if it doesn't it will at east tell why those packages can't be upgraded.

---

### Post by solar george on 2007-07-12
You could also try,
```
sudo apt-get dist-upgrade
```

---

### Post by Inxsible on 2007-07-12
> **zvacet said:**
> So,say yes.Ubuntu-desktop is meta-package and you can remove it with no problem,but you need it if you want to do upgrade.

But I already run 7.04 and i dont intend to upgrade to Gutsy just yet. and I dont want ubuntu-desktop because there are many apps which come along with it, which i dont use at all.

I shall try what mcduck suggested and get back to you guys.

---

### Post by Inxsible on 2007-07-12
Well i went to synaptic and the upgradeable (upstream) and marked the 3 packages for upgrade. It asked me if it was ok to remove the following packages
compiz
compiz-gnome-config
compiz-gtk
desktop-effects

I said yes and everything worked out. I guess it replaced the above 4 with the 3 listed in my first post. Hopefully nothing is broken :)
This will probably remove the partial upgrade message i kept getting...but I will now have to wait for automatic updates to find out :)

Thanks mcduck !!

---

