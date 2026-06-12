---
title: "Installing different desktop environments"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-09-15
Hi guys!

I just installed Xubuntu, but I would like to be able to switch to the KDE or GNOME environments if I'd like to.

How do I go about installing the additional environments?

Thanks!

---

### Post by Brunellus on 2006-09-15
> **Stone9 said:**
> Hi guys!

I just installed Xubuntu, but I would like to be able to switch to the KDE or GNOME environments if I'd like to.

How do I go about installing the additional environments?

Thanks!
for KDE:

sudo aptitude install kubuntu-desktop

for GNOME:

sudo aptitude install ubuntu-desktiop

for other DEs and window managers, see relevant howtos and/or wiki pages.

---

### Post by Metacarpal on 2006-09-15
Just like he said, but before you install:
```
sudo aptitude update
```
just to make sure you're getting the latest and greatest.

---

### Post by Stone9 on 2006-09-15
Great! Thanks a lot guys!

---

### Post by Stone9 on 2006-09-15
What would the code be if I already have the .iso of those distros on a CDs?

Thanks!

---

### Post by Brunellus on 2006-09-15
> **Stone9 said:**
> What would the code be if I already have the .iso of those distros on a CDs?

Thanks!
same command;  the install discs of each should act as APT repositories--but apt will prefer the online repositories, given a choice, since the online ones will be fresher.

---

### Post by aysiu on 2006-09-15
> **Stone9 said:**
> What would the code be if I already have the .iso of those distros on a CDs?

Thanks!
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Works for only the **Alternate CD**. It will not work for the **Desktop CD**.

---

### Post by Brunellus on 2006-09-15
good catch aysiu.

---

### Post by Stone9 on 2006-09-15
Great tips guys! Is there anything I should worry about concerning having duplicate applications installed for the same purpose.

Also, how does Konqueror compare to Firefox or Opera?

Thanks!

---

### Post by bt224 on 2006-09-15
Not to highjack the thread, but if you have multiple desktops environments (KDE and Gnome), how do you switch between them, and does each save their own settings?

---

### Post by aysiu on 2006-09-16
> **Stone9 said:**
> Great tips guys! Is there anything I should worry about concerning having duplicate applications installed for the same purpose. Yes--cluttered menus! But you can delete menu entries if they annoy you.

> 
Also, how does Konqueror compare to Firefox or Opera?

Thanks! Konqueror's a pretty good browser, a bit like Opera, in that it's fully featured but not very extensible. I don't use it, though, as I use Kate in KDE to edit HTML files, and it won't let me have Kate be the default editor for HTML file *and* let me browse to HTML sites. Weird, I know.

> **bt224 said:**
> Not to highjack the thread, but if you have multiple desktops environments (KDE and Gnome), how do you switch between them, and does each save their own settings? You pick the session as login and each does have its own settings. See details at the end of this page: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

