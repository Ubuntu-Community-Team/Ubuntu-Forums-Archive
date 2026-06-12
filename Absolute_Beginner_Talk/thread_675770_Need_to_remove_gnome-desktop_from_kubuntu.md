---
title: "Need to remove gnome-desktop from kubuntu"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Dazed_75 on 2008-01-23
A friend has kubuntu on her laptop and installed gnome-desktop so as to more easily work a course on the ubuntu desktop.  Unfortunately, while in gnome, running some kde apps even by accident brings up a window the user cannot move or close and whose menu items are all grayed out.  I have duplicated this on a test machine and verified that installing ubuntu-desktop on the kubuntu system does not cause this problem.

The problem is that uninstalling gnome-desktop does not remove the hundred or so other components it installed and I am unclear how to do that before installing ubuntu-desktop for her.

Looking for any good ideas on how to do this reasonable cleanly and [hopefully] easily before resorting to brute force which could take a long time and be error prone.

---

### Post by dpar on 2008-01-23
You could try this.....

[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by Dazed_75 on 2008-01-23
Close perhaps.  But since we installed gnome-desktop using adept while (from within KDE) the first half of that reference does not apply per that page.  The second half gives very long command lines to paste for removing ubuntu-desktop or xbuntu-desktop, but none for gnome-desktop.  It also does not say anything about how to generate those long command lines for removing a different desktop installed by adept.

Thanks for trying, it is very close, but it looks like we will have to do it the hard way with LOTS of manual removes and hope for the best.

Oh yes, I did think of another very messy method that might work.  That is to not remove anything, install ubuntu-desktop and just never select the straight gnome session at logon.  One might even find where to edit that menu and remove the Gnome entry.  What I don't like is not knowing how much junk might be left behind.

---

### Post by wolfen69 on 2008-01-23
did you do
```
sudo apt-get autoremove
```
you can also run deborphan and gtkorphan(gui front end) to clean up unused files.

---

### Post by dpar on 2008-01-23
I believe ubuntu desktop IS gnome. Kubuntu is KDE.
Also, it's not that hard to select,copy,and paste those commands.

---

### Post by Dazed_75 on 2008-01-23
wolfen69,

Thanks for the reply. I had not tried that but before I had to run out for a bit I had thought I should try
       sudo apt-get remove gnome-desktop autoremove
or some variation (syntax was not clear)

The way I read the man page looked like the autoremove option would need to know for what package the dependents were installed.

Anyone know for sure?

---

### Post by Dazed_75 on 2008-01-23
Actually dpar, that is why we had trouble.  We thought so too.  They are definitely not the same.  Apparently ubuntu uses a customized version of gnome.  So adding gnome-desktop works but breaks things while adding ubuntu-desktop (which certainly is gnome based) works without breaking things (although it does have some surprising side effects).

---

### Post by stchman on 2008-01-23
> **Dazed_75 said:**
> A friend has kubuntu on her laptop and installed gnome-desktop so as to more easily work a course on the ubuntu desktop.  Unfortunately, while in gnome, running some kde apps even by accident brings up a window the user cannot move or close and whose menu items are all grayed out.  I have duplicated this on a test machine and verified that installing ubuntu-desktop on the kubuntu system does not cause this problem.

The problem is that uninstalling gnome-desktop does not remove the hundred or so other components it installed and I am unclear how to do that before installing ubuntu-desktop for her.

Looking for any good ideas on how to do this reasonable cleanly and [hopefully] easily before resorting to brute force which could take a long time and be error prone.

Use autoremove.

```
sudo apt-get autoremove ubuntu-desktop
```

This will remove the dependencies as well.

---

