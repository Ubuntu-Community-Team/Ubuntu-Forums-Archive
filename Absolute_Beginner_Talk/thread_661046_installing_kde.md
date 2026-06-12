---
title: "installing kde"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Benbow on 2008-01-07
I am running gnome and I would like to have the option of using either gnome or kde. How do I do this?

---

### Post by perlluver on 2008-01-07
Install kdecore, or kubuntu-desktop.  Then on the GDM login screen in sessions you can pick KDE or Gnome.

---

### Post by snickers295 on 2008-01-07
install:
```
sudo apt-get install kubuntu-desktop
```
and then in the login options choose KDE as the session.

---

### Post by philinux on 2008-01-07
You would be advised to use aptitude to install it if you later wish to remove it.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by cartisdm on 2008-01-07
I just did this as well yet, my session once logged in isn't KDE.  I get the "Kubuntu" splash screen, and the KDE login screen and I can select it when I login so I know it's there, but my desktop looks the exact same as with GNOME.  The only difference is a bunch of stuff in my applications start with a K!

---

### Post by Incense on 2008-01-07
> **cartisdm said:**
> I just did this as well yet, my session once logged in isn't KDE.  I get the "Kubuntu" splash screen, and the KDE login screen and I can select it when I login so I know it's there, but my desktop looks the exact same as with GNOME.  The only difference is a bunch of stuff in my applications start with a K!

Are you clicking on Session and selecting KDE from the log in screen? It sounds like it is defaulting to your Gnome desktop.

---

### Post by cartisdm on 2008-01-07
weird, I rebooted (a second time) and this time when I logged in everything went as it should.  But thanks!

---

### Post by dwhitney67 on 2008-01-07
I recently installed KDE, and to do this, I ran a different command that posted previously.  I used:

```
$ sudo apt-get install kde
```

Once I logged out, I saw the typical GDM login problem that Ubuntu provides, and then the option to select either Gnome or KDE from the "Session" menu.

P.S.  I was disappointed with KDE.  To many applications clutter the pull-down menus once I logged in.  And no wireless!  Needless to say, not only did I remove KDE, but I removed the entire OS.  I installed Fedora 8 in its place.

---

### Post by snickers295 on 2008-01-07
> **dwhitney67 said:**
> I recently installed KDE, and to do this, I ran a different command that posted previously.  I used:

```
$ sudo apt-get install kde
```Once I logged out, I saw the typical GDM login problem that Ubuntu provides, and then the option to select either Gnome or KDE from the "Session" menu.

P.S.  I was disappointed with KDE.  To many applications clutter the pull-down menus once I logged in.  And no wireless!  Needless to say, not only did I remove KDE, but I removed the entire OS.  I installed Fedora 8 in its place.
Thats why people suggest using only one of the two.

---

