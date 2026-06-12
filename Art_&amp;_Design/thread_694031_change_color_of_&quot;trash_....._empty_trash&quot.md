---
title: "change color of &quot;trash ..... empty trash&quot; bar"
date: 2008-02-11
forum: Art &amp; Design
---

### Post by duncan.hawthorne on 2008-02-11
a small request, but i'd like to know to complete my theme.
when you go into trash: you see a bar at the top which is light blue, color #A7C5E0. this same color appears in cd/dvd creator, and search inside nautilus, and probably in other places...
any idea how to change it?

---

### Post by CarpKing on 2008-02-11
I don't know of any way to change that.  If you don't get any responses from people that do, you should file a bug against Nautilus.  This bar should really take it's color from the GTK theme automatically.

---

### Post by Risujin on 2008-03-10
I was looking for this too, from [http://mail.gnome.org/archives/nautilus-list/2005-December/msg00077.html](http://mail.gnome.org/archives/nautilus-list/2005-December/msg00077.html):

> style "blah" {
      bg[NORMAL] = "red"
}
widget "*.nautilus-extra-view-widget" style:highest "blah"

---

### Post by CarpKing on 2008-03-11
What GTK theme are you using?  I'm using Clearlooks, and my bar does follow my colorscheme (currently green).

---

