---
title: "Kubuntu vs. Ubuntu"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by ncab23 on 2007-12-15
So I've used ubuntu before some, and now I'm going to install al linux OS again, but I'm trying to decide whether to go with the gnome or the kde interface. What i'm wondering is if I install one, can I convert to the other without much trouble, or will I have to completely reinstall it to go from one to the other (ex. Ubuntu to Kubuntu)

---

### Post by LaRoza on 2007-12-15
> **ncab23 said:**
> So I've used ubuntu before some, and now I'm going to install al linux OS again, but I'm trying to decide whether to go with the gnome or the kde interface. What i'm wondering is if I install one, can I convert to the other without much trouble, or will I have to completely reinstall it to go from one to the other (ex. Ubuntu to Kubuntu)

If you install Ubuntu, you can install KDE with:

```

sudo aptitude install kde-core

```

You can install all of Kubuntu on Ubuntu with:
```

sudo aptitude install kubuntu-desktop

```

The second one will result in all of Kubuntu's apps being installed, I suggest using the first one, then selectively install KDE apps.

---

### Post by dgoodma on 2007-12-15
You might just evaluate which one you want by using the Live CDs.

I did that, and decided on Ubuntu, it seemed to be more straight-foward on my laptop with the Wireless card, it just connected; never did see where the wireless was under Kubuntu. I did not look very far though.

---

### Post by taurus on 2007-12-15
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by Sef on 2007-12-15
You can have both:  

```
sudo apt-get install ubuntu-desktop
```

If you use Kubuntu, or

```
sudo apt-get install kubuntu-desktop
```

if you use Ubuntu

---

### Post by flamelab on 2007-12-15
You should only install **ONE **desktop ( the default )on an operating system , especially Ubuntu here .
When you have two or more installed , the system loads libs for ALL of the desktops and that can seriously cause a great lag on your system .

---

### Post by ncab23 on 2007-12-15
great thanks for the information and advice everyone

---

