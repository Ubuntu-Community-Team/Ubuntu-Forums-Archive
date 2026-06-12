---
title: "Detailed List View Column Colors"
date: 2007-06-27
forum: Art &amp; Design
---

### Post by kadath on 2007-06-27
I'm making a GTK theme (based on Murrine engine), and it's nearly complete except for one problem: I don't know how to edit the colors of the columns in the detailed list view (they alternative between white and light grey in most themes).

If anyone can help me out with this, I'd be grateful.

---

### Post by bvc on 2007-06-28
search some theme gtkrc's for
"odd"
"even"
"row"
I usually put it at the top just above the theme colors.
[http://gnome-look.org/usermanager/search.php?username=bvc&action=contents](http://gnome-look.org/usermanager/search.php?username=bvc&action=contents)

---

### Post by kadath on 2007-06-28
> **bvc said:**
> search some theme gtkrc's for
"odd"
"even"
"row"
I usually put it at the top just above the theme colors.
[http://gnome-look.org/usermanager/search.php?username=bvc&action=contents](http://gnome-look.org/usermanager/search.php?username=bvc&action=contents)

Thanks for the help! I'll try this when I get home :D

---

### Post by bvc on 2007-06-28
well, I'm home now. This is what you are looking for
  GtkTreeView::odd_row_color = "#f1f5eb"
  GtkTreeView::even_row_color = "#ffffff"

and these are links in gtk apps like the silly and ugly links in the media players like rhythmbox.
  GnomeHRef::link_color		="#82985C" 
  GtkIMHtmlr::hyperlink-color	="#82985C"

---

### Post by kadath on 2007-06-28
> **bvc said:**
> well, I'm home now. This is what you are looking for
  GtkTreeView::odd_row_color = "#f1f5eb"
  GtkTreeView::even_row_color = "#ffffff"

and these are links in gtk apps like the silly and ugly links in the media players like rhythmbox.
  GnomeHRef::link_color		="#82985C" 
  GtkIMHtmlr::hyperlink-color	="#82985C"

Thanks a lot for the help! Looking at the stuff you posted on GNOME-Look, you definitely look like an expert on this stuff.

---

### Post by bvc on 2007-06-29
Thanks!...but it didn't come easy, and I don't think anyone can be an expert, except maybe a developer, and they don't communicate with themers, mostly. It took years to hack around the messy-non-theme-friendly code.

---

