---
title: "Gnome vs. KDE"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by msmarti58 on 2007-09-20
Can someone tell me why Gnome works seamlessly on my machine and yet KDE gives me all kinds of grief? Among my problems - software hanging, unable to mount my external USB Drive, slow behavior. It seems odd, the Kubuntu ppl told me it's all the same basically.

---

### Post by buzzmandt on 2007-09-20
what are your system specs?
and how did you install, from kubuntu cd or did you install gnome and add kubuntu-desktop, etc?

Kde needs a bit more from resources, gnome is a bit lighter and xfce is lighter still

---

### Post by kellemes on 2007-09-20
KDE offers a lot more stuff out of the box and therefor will be a littlebit more recourse-hungry, still.. when configured right you won't have to notice a difference with Gnome at all. So try to disable some fancy stuff from the control center and please post specific issues you have with softwarepackages hanging etc.. Often starting packages from the terminal gives informative output you may use to debug or post so we can help.

Edit: System-specs indeed are helpful.

---

### Post by justin whitaker on 2007-09-20
> **msmarti58 said:**
> Can someone tell me why Gnome works seamlessly on my machine and yet KDE gives me all kinds of grief? Among my problems - software hanging, unable to mount my external USB Drive, slow behavior. It seems odd, the Kubuntu ppl told me it's all the same basically.

I'm a Kubuntu user....and both Ubuntu and Gnome work fine on my machine. What are your system specs?

You can pretty much tweak everything in KDE. A fine resource is here:

[https://help.ubuntu.com/community/KubuntuOptimization](https://help.ubuntu.com/community/KubuntuOptimization)

Mounting external drives is not so tough: sudo apt-get install ntfs-3g, and mount/unmount via the command line. You can edit fstab so they automount as well. Ok, ok, there is also a GUI for it if you insist. It's in add/remove programs under...system? :)

---

### Post by mjwhitfield on 2007-09-20
> **kellemes said:**
> KDE offers a lot more stuff out of the box and therefor will be a littlebit more recourse-hungryKDE is less resource hungry than GNOME iirc.

---

### Post by rsambuca on 2007-09-20
> **mjwhitfield said:**
> KDE is less resource hungry than GNOME iirc.

Uh, I don't think so!

---

### Post by hyper_ch on 2007-09-20
ntfs-3g is not required to mount external drives... ntfs-3g is required if you want to write to ntfs drive (at your own risk)

---

### Post by justin whitaker on 2007-09-20
> **hyper_ch said:**
> ntfs-3g is not required to mount external drives... ntfs-3g is required if you want to write to ntfs drive (at your own risk)

This is true...I just assume that people want to write to their drives as well as read them. :)

---

### Post by TenPlus1 on 2007-09-20
Gnome generally uses 140mb memory when installed...

KDE uses up to 320mb memory after installed...

XFCE uses only 84mb...

I'd stick wiht Gnome, it works and you dont really need all the fanciness of KDE to use a desktop...

---

### Post by ukripper on 2007-09-20
> **mjwhitfield said:**
> KDE is less resource hungry than GNOME iirc.

is it a joke? Please tell me it is!

---

### Post by mjwhitfield on 2007-09-20
> **ukripper said:**
> is it a joke? Please tell me it is!jesus call off the firing squad.

I thought I read that somewhere here, lemme dig around and see what I can find.

---

### Post by mjwhitfield on 2007-09-20
> **TenPlus1 said:**
> Gnome generally uses 140mb memory when installed...

KDE uses up to 320mb memory after installed...

XFCE uses only 84mb...

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)

> "Very plain" means minimal functionality. In KDE's case there there was only the basic desktop and very basic panel applets like the taskbar, pager and clock. Similarly with other desktops. The desktops were fully functional though, without any "cheating" like I did during the last Akademy talk. And the numbers are:


```
Desktop	Usage	Diff 
KDE	60.4 (57.6)	29.1 (14.4) 
GNOME	74.8 (71.2)	43.5 (28) 
Xfce	47.9 (52.6)	16.6 (9.4) 
WMaker	36.9 (47.0)	5.6 (3.8)
```

---

### Post by mjwhitfield on 2007-09-20
More stuff.

[QUOTE=http://ktown.kde.org/~seli/memory/desktop_benchmark.html]This one admitedly may look a lot like I'm trying to cheat. In this case KDE running KDE applications, GNOME running GNOME applications and Xfce running generic applications will be compared. Xfce will be running generic applications simply because it doesn't have any comparable on its own - no web browser, no office suite, no mail client. In KDE's case these are going to be Konqueror, KWord and Kontact, in GNOME's case Epiphany, Abiword and Evolution and Xfce will be accompanied by the most known independent applications, that is Firefox as a web browser, OpenOffice.org as office suite and Thunderbird a mail client.[/QUOTE]

```
Desktop	Usage	Diff 
KDE + KDE apps	143.2 (117.7)	111.9 (74.5) 
GNOME + GNOME apps	174.8 (149.3)	143.5 (106.1) 
Xfce + 3rd party apps	206.8 (135.7)	175.5 (92.5)
```

---

