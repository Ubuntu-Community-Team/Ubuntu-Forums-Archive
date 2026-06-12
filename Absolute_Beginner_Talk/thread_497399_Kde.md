---
title: "Kde"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by 3enith on 2007-07-10
do we have KDE in ubuntu 7.04 too?

---

### Post by jaytek13 on 2007-07-10
You can run 

sudo apt-get install kubuntu-desktop

Or you can just install Kubuntu.

---

### Post by Nekiruhs on 2007-07-10
Yep. You can install normal Ubuntu and do a sudo apt-get install kubuntu-desktop and you will have a choice when you login of Gnome or KDE. Or you could install Kubuntu by itself from the Kubuntu CD.

**EDIT:** Grrr... I'm getting slow...

---

### Post by AlexenderReez on 2007-07-10
better install kde with

> sudo aptitude install kubuntu-desktop

because if you don't like just


> sudo aptitude remove kubuntu-desktop

will remove all package that you have install for kde or kubuntu

---

### Post by Malibu Illusion on 2007-07-10
So will:

```
apt-get remove kubuntu-desktop
apt-get autoremove
```

apt-get, aptitude doesn't make a difference in *ubuntu.

---

### Post by ozzyprv on 2007-08-21
I tried "sudo aptitude install kubuntu-desktop". It was taking more than an hour to install and then I canceled and removed.

Is it normal (installation > 1h)?

Any other way to install KDE (all I want is Konqueror) in Ubuntu 7.04?

Thanks.

---

### Post by cookies on 2007-08-21
> **ozzyprv said:**
> I tried "sudo aptitude install kubuntu-desktop". It was taking more than an hour to install and then I canceled and removed.

Is it normal (installation > 1h)?

Any other way to install KDE (all I want is Konqueror) in Ubuntu 7.04?

Thanks.


It's like 150+ packages. It'll take a nice long time.

I think Konqueror can be installed alone. Not sure though.

---

### Post by Belliinator on 2007-08-21
Hey you can just get it from synaptic, just search for Konsole and tick the box to download.

Or try: ```
sudo aptitude install konsole
```

Hope it helps

does anyone know how you can combine ubuntu AND kbuntu cds so you have a dual desktop without using up all the bandwidth?

---

### Post by cookies on 2007-08-21
> **Belliinator said:**
> Hey you can just get it from synaptic, just search for Konsole and tick the box to download.

Or try: ```
sudo aptitude install konsole
```

Hope it helps

does anyone know how you can combine ubuntu AND kbuntu cds so you have a dual desktop without using up all the bandwidth?


Make that sudo aptitude install konqueror. ;) The OP wants Konqueror.

---

### Post by Belliinator on 2007-08-21
Sorry my bad. I got muddled in my train of thought.

---

### Post by ubuntu27 on 2007-08-21
Yes you can install [KDE desktop environment ]("http://www.kde.org/") in Ubuntu, you can install [XFCE]("http://www.xfce.org/") too!

 you can install KDE in Ubuntu by: 
```
sudo aptitude install kubuntu-desktop
```

Or you can download them here:
[Kubuntu]("http://www.kubuntu.org/"), Ubuntu with KDE

[Xubuntu]("http://www.xubuntu.org/"), Ubuntu with [XFCE]("http://www.xfce.org/")


PS: [Ubuntu]("http://www.ubuntu.com/") uses [GNOME]("http://www.gnome.org/").

---

### Post by krazytekn0 on 2007-08-22
> **AlexenderReez said:**
> better install kde with



because if you don't like just




will remove all package that you have install for kde or kubuntu

Won't this only remove the meta package?
This won't actually remove KDE, Just the package that depends on KDE

---

