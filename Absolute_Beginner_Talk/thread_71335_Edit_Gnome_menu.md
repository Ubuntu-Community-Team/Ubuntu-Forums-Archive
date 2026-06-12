---
title: "Edit Gnome menu"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by Nachtegaal on 2005-10-03
Is it possible to edit the Places & Sytem Menu, just like you van edit the ApplicationsMenu with SMEG.

---

### Post by Ampersand on 2005-10-03
You can add to the Places menu using the Bookmarks menu in Nautilus. Open the folder you want to add in the file manager, then Bookmarks - Add Bookmark.

---

### Post by Stoff on 2006-01-09
hello,

i am searching the forum for any editting the places menu related threads.
most authors say something about using nautilus' bookmark function in order to add/remove folders. 
where is that bookmark function? where and how can i access this menu in nautilus?

christoph

---

### Post by Arktis on 2006-01-09
Open nautilus, and in the nautilus top menu bar, go to the Bookmarks menu and click "Add Bookmark".

Heheheh :smile:

---

### Post by Stoff on 2006-01-09
man, where on earth is this bookmark menu? i'm using nautilus 2.10.0. my menu shows file edit view places help. that's it. even ctrl+b doesn't work.
do i have a wrong version or something?

christoph

---

### Post by Arktis on 2006-01-09
Seems like it.  My Version shows as 2.12.1  I'm using Ubuntu Breezy Badger.  Are you using the older Hoary Hedgehog version of Ubuntu?

---

### Post by Stoff on 2006-01-09
yes, i am using the Hoary Hedgehog version.
what can i do then? install a newer version of nautilus?
my synaptic package manager only lists version 2.10.0

so this implies another question: how do i change to a newer ubuntu version? or is this really necessary?

in the meantime, is there an easy way to edit the places menu without nautilus?

---

### Post by Arktis on 2006-01-09
Two options:

1.)  You can dist-upgrade to breezy using apt-get (I don't advise this as it can leave your system in disarray).

```
sudo gedit /etc/apt/sources.list
```

Replease “hoary” with “breezy” save the file and then run the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

2.)  Just do a fresh install of breezy after backing up stuff like your bookmarks, xorg.conf (if you made any changes to it you want to keep) and anything else you want to save.  [http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download)

---

### Post by DonVla on 2006-01-10
here from the gnome-page:

[http://www.gnome.org/learn/users-guide/2.10/ch05.html](http://www.gnome.org/learn/users-guide/2.10/ch05.html)

---

### Post by Wolki on 2006-01-10
[QUOTE=Stoff]in the meantime, is there an easy way to edit the places menu without nautilus?[/QUOTE]

Yes. You can edit the places menu by opening the file selector (the dialog you get whan you choose "open file" in a gnome application). You have some shortcuts on the left side. Drag directories there (or use the add/remove buttons) to edit these shortcuts. The Places menu wil be updated accordingly.

---

