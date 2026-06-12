---
title: "KDE and Gnome on the same Ubuntu install ?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by foundation on 2007-06-19
So, say I want to use both is there a way have both completely installed and be able to choose which one I want to use when I first go into Ubuntu ?

Or, if that's not possible is there a way to 'switch' my current install (Gnome) to KDE without my system exploding and have the ability to easily switch back ?

---

### Post by sad_iq on 2007-06-19
Try ```
sudo apt-get install kubuntu-desktop
``` That will install kde and will let you choose witch one to use!!!

---

### Post by logos34 on 2007-06-19
just install kubuntu-desktop metapackage.  On your logon screen you'll have a choice of either (or more if you install xubuntu, edubuntu, etc).  I've installed and ripped out kde without borking anything, aside from the font size on the logon screen being so small that it's casuing me to go blind trying to read it.

---

### Post by Sweet Mercury on 2007-06-19
> **sad_iq said:**
> Try ```
sudo apt-get install kubuntu-desktop
``` That will install kde and will let you choose witch one to use!!!

To add to that. After that package installs, you have to log out of your GNOME session. In the login screen, there will be either an options menu with a "sessions" entry, or a dedicated sessions button. Click either of those, and you can pick between GNOME and KDE.

A few different dialog boxes will pop up; read them; they're pretty self explanatory.

---

### Post by foundation on 2007-06-19
That easy, eh ? Awesome, I'll go try it out soon.

Thanks guys.

---

### Post by zvacet on 2007-06-19
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by Sweet Mercury on 2007-06-19
> **foundation said:**
> That easy, eh ? Awesome, I'll go try it out soon.

Thanks guys.

For the most part, yeah. Although I recently sorta broke my XFCE session, but that's because of my tinkering, I think.

It becomes more difficult, I've found out, when you start messing with the sessions and environments themselves. But as far as just grabbing a new DE, it should be no problem.

Good luck!

---

