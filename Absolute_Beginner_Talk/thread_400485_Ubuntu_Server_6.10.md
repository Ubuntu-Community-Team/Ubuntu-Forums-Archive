---
title: "Ubuntu Server 6.10"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by jenny07 on 2007-04-03
Is there a GUI desktop interface for the ubuntu server edition?

Jenny
:KS

---

### Post by taurus on 2007-04-03
Yes, you just have to install either Gnome, KDE, XFce4, fluxbox, etc.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop <- for Gnome
sudo aptitude install kubuntu-desktop <- for KDE
sudo aptitude install xubuntu-desktop <- for XFce4
```

---

### Post by compmodder26 on 2007-04-03
There can be, if you install "ubuntu-desktop" after you install the server edition.  But, if you want that, you might as well download the desktop version.

Also, if you are using this for a production server, I would recommend using Dapper (6.06).  It is a long term support release that will be supported through 2011 (server edition only, desktop version only through 2009).  Edgy's (6.10) support lifetime will only last through 2008.  I personally prefer not having to upgrade my servers every 18 months.

---

### Post by jenny07 on 2007-04-03
...but the desktop version doesn't contain LAMP, or does it?


How do I run the desktop version after install?

Jen
:KS

---

### Post by compmodder26 on 2007-04-03
There isn't an option at startup like there is with the server, but you can most certainly install the necessary LAMP programs after the install completes.  Just search for them in synaptic (apache2, mysql, php) (note, if you are looking for perl for the P in LAMP, perl is already installed).

If you choose to install the server version then add the desktop later (per the commands provided by taurus above), the desktop should start automatically (I believe.  Someone correct me if I'm wrong).

---

