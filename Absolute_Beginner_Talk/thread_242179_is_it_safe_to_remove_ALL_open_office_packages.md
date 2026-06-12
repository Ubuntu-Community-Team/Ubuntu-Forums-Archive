---
title: "is it safe to remove ALL open office packages?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-23
As the title sujests i`d like to know if it`s safe to remove ALL entrys of the Open Office suite?
It`s not something needed on the pc in question so am trying to remove as many pointless apps as possible.......WITHOUT there being any adverse effects on the rest of the system of course.The whole "dependancy" thing can be a bit intimidating at times.
Also if i remove anything and it leaves "residual packages" in synaptic, is it also ok to remove them or are they kept back for a reason?Are there possibly only "residual packages" because some where installed with Add/Remove?..(cant quite recall?)

I was under the assumption that synaptic was just a gui frontend(think thats the term)for "Aptitude" and that aptitude removed ALL dependancys unlike say apt-get?.....

---

### Post by mlind on 2006-08-24
Yes it's safe, if you can remove packages in a way that all other package are satisfied (no dependency problems).

This would purge all package that have openoffice in their name. It probably leads to dependency problems, but you can try resolving it.
```

sudo aptitude purge $(dpkg -l | grep openoffice | awk '{ print $2 }')

```
Try removing only openoffice packages first that don't cause any trouble. You can always install those back if you change your mind. Most of the openoffice packages and language-support packages should be safe to remove.



Packages that are removed, but not purged, leave "residual config". This means that important configuration files are left installed, so that your settings persist if you decide to install the package back. Purge removes this files too.

You can view these also with:
```

dpkg -l | grep "^rc "

```

And remove all package that have left "residual config" behind
```

sudo dpkg -P $(dpkg -l | grep "^rc ")

```

And yes, synaptic is one of the package management interfaces. aptitude removes package dependencies on removal too, but I guess only if package has been installed using aptitude first..

---

