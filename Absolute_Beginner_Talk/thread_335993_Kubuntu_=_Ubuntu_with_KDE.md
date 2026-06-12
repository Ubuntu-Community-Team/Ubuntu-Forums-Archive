---
title: "Kubuntu = Ubuntu with KDE?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Lightstar on 2007-01-11
I'm half-new to this... tried a bunch of linux in the past, but never for more than a week.  I tried Ubuntu once and loved it, so I'm coming back to Ubuntu permanently.  So what's with Kubuntu and Xubuntu and etc etc etc?

Kubuntu is the same as Ubuntu, except it has KDE pre-installed as default?  and Ubuntu has Gnome as default?  that's all?

If I get Ubuntu and just install KDE, will I have the same result as installing Kubuntu?

I see a bunch of polls about "which *buntu did you install?" so I'm thinking they must be 2 different linux.  Anyway, just want to make sure which direction I need to jump when I format.  If it's the same I'll just get Ubuntu and installed KDE if I'm not happy with Gnome.

---

### Post by IYY on 2007-01-11
Basically, yes. There are some other subtle differences in the exact software that's installed on each one, but it's mostly just Gnome vs. KDE. They are different distributions in the sense that you can get them on different CDs, but you can always add KDE to Ubuntu with 

```
sudo apt-get install kubuntu-desktop
```

and Gnome to Kubuntu with


```
sudo apt-get install ubuntu-desktop
```

Something like

```
sudo apt-get install gnome
```

should also work, but the other method is better.

---

### Post by MkfIbK7a on 2007-01-11
try looking through these threads
[http://ubuntuforums.org/showthread.php?t=335283](http://ubuntuforums.org/showthread.php?t=335283)
[http://ubuntuforums.org/showthread.php?t=327044](http://ubuntuforums.org/showthread.php?t=327044)
incidentally i started both of those threads but lots of people answered well:biggrin:

---

### Post by bikeboy on 2007-01-11
> **Lightstar said:**
> I'm half-new to this... tried a bunch of linux in the past, but never for more than a week.  I tried Ubuntu once and loved it, so I'm coming back to Ubuntu permanently.  So what's with Kubuntu and Xubuntu and etc etc etc?

Kubuntu is the same as Ubuntu, except it has KDE pre-installed as default?  and Ubuntu has Gnome as default?  that's all?

Yep...well almost.

> If I get Ubuntu and just install KDE, will I have the same result as installing Kubuntu?

Not quite. Kubuntu is tailored for KDE use with regard to apps etc. If you install Ubuntu then add KDE you will have a large combination of Gnome and KDE programs. This could mean some messy menus that need fixing and stuff, which might not suit you (but it might).

My advice is to decide which desktop you prefer (maybe by installing both to begin with), but after that install your favourite one and add any programs you prefer from the other desktop manually. eg. Install Ubuntu but add K3B for cd burning (it's a common favourite). That will add some KDE stuff but only the bare minimum.

---

### Post by aysiu on 2007-01-11
From [Kubuntu's website](http://www.kubuntu.org/faq.php#whatiskubuntu): > Kubuntu is the first Ubuntu derived distribution. Our Kubuntu CDs are made up of Ubuntu's base plus KDE. You can get exactly the same effect by installing Ubuntu and adding the KDE packages (and removing the Gnome packages) from the Ubuntu archives.

---

### Post by x64Jimbo on 2007-01-11
The best way to find out the difference is to get this:
[http://www.ubuntu-hr.org/ningi/](http://www.ubuntu-hr.org/ningi/)
It's basically all the Ubuntu versions in one DVD image. Play around with all the different versions until you find one you like, then go with that.

---

### Post by pcomelade on 2007-01-11
If you use KDE on Ubuntu don't forget to add the Kubuntu "repos" to the source.list:

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

Cheers,

M;

---

