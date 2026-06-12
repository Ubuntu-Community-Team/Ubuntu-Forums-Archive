---
title: "Synaptic vs. Adept"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by tadashi on 2006-02-22
I am running Kubuntu and the package manager in my menu is Adept.  Will Synaptic run in KDE or is that a Gnome thing?  Also, is it any better or just a different flavor of a package manager?  Adept can be annoying because I just get a giant list of stuff sorted by name (not by application, docs, etc) or is there a way to sort in that manner in Adept?

---

### Post by 5-HT on 2006-02-22
There should be no problem running Synaptic from KDE (it'll just need some GNOME libs).

About package managers...I prefer Aptitude.

It's has both GUI (within console) and CLI interfaces, and automatically marks packages as either manually installed or automatically installed (dependencies).

So when it comes to uninstalling, all of the packages required by whatever you are uninstalling that were installed simply as dependencies that are no longer needed are uninstalled as well.

HTH

---

### Post by aysiu on 2006-02-22
Synaptic lets you search by different criteria. Adept has "filters," which suck because they take a lot longer to filter out stuff.

You can also mark packages for "reinstallation" in Synaptic, which you can't do in Adept.

Browsing and searching for packages is a lot faster and easier than "filtering," in my opinion.

And, yes, Synaptic (and every "Gnome application") works just fine in KDE.

---

### Post by tadashi on 2006-02-22
I am assuming that Kubuntu will not have a problem if I use more than one of them or once I pick one I have to stick with it?

---

### Post by 5-HT on 2006-02-22
It's no problem using both, either, or swtiching between them (they all use the same backend).
The only limitation is that you can't use both at the time time (i.e. installing/removing  diff packages simultaneously from diff package managers).

One note though: 

If you give Aptitude a try, you need to install the packages with it in order to take advantage of the automagic dependency marking and subsequent automagic removal with Aptitude.

---

### Post by aysiu on 2006-02-22
[QUOTE=tadashi]I am assuming that Kubuntu will not have a problem if I use more than one of them or once I pick one I have to stick with it?[/QUOTE] You can use whichever one suits you're fancy. You *cannot* have both open simultaneously, though.

---

### Post by Jucato on 2006-02-22
Just as you can't have Synaptic/Adept open and use apt-get/aptitude at the same time. 

Anyway, yeah, Synaptic will work very well in Kubuntu. In fact, for now I recommend it more than Adept, or until I see the new Adept in Dapper. If you really want to stick to KDE apps, there's also KPackage, which is KDE's package manager. But, IMHO, Synaptic is better than either of these two.

---

