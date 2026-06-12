---
title: "activate kde"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-09-25
Hi everyone,

I am currently using GNOME in ubuntu. I want to move to KDE. Can someone tell me how to 
do that please.. !

Thanks.

---

### Post by LaRoza on 2007-09-25
```

sudo aptitude install kde-core

```

When you log on, change the "Session" to kde.

---

### Post by anaconda on 2007-09-25
hmm..

I thought it was:
sudo apt-get install kubuntu-desktop

What is the difference? I have always used this and it works like it should.

and the same thing with this change the session to kde..

---

### Post by LaRoza on 2007-09-25
They are not the same:

kubuntu-desktop will get you kubuntu. Which means you get everything, apps and all.

kde-core will get you less.

The OP wanted KDE, not Kubuntu, so I mentioned the package for what was wanted.

@OP, if you want all of Kubuntu's apps and features, kubuntu-desktop is the package to get.

You can run kde-core now, then get kubuntu-desktop later. kde-core is smaller.

---

### Post by nvteighen on 2007-09-25
Please, do what LaRoza told you, install kde-core. To install kubuntu-desktop can be a bit problematic, specially with menus (you'd get GNOME and KDE apps mixed). And never think to install the "kde" package, which is even bigger than kubuntu-desktop... and broke my fonts in GNOME. (Summary: kde-core < kubuntu-desktop < kde; begin installing the smallest)

---

### Post by LaRoza on 2007-09-25
> **nvteighen said:**
> Please, do what LaRoza told you, install kde-core. To install kubuntu-desktop can be a bit problematic, specially with menus (you'd get GNOME and KDE apps mixed).

...unless you want K apps. If you want a specific app, you can install it, all KDE apps I have used, worked fine in GNOME in any DE.

---

### Post by path_finder on 2007-09-26
Thank you so much LaRoZa. aptitude kde- core is ideal for my slow dial-up connection.
I won't be able to see working that command ends with -desktop through out my life time with my slow connection.

Thanks everyone who read this post ... !

---

### Post by ekss on 2007-09-26
thanx LaRoZa.

---

