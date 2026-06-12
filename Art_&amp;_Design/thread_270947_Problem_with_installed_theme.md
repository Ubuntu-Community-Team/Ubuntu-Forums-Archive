---
title: "Problem with installed theme"
date: 2006-10-04
forum: Art &amp; Design
---

### Post by pak33m on 2006-10-04
Hello,

I just installed the theme Cillop found here:

[http://www.gnome-look.org/content/show.php?content=46507](http://www.gnome-look.org/content/show.php?content=46507)

However, I cannot rid the panel sides of the theme color.  I've attached a screenshot of it.  I would like to have the panel be transparent, but the color is still there in the panel.  In the link above the creator suggests having a few engines installed.  I believe that I have the Clearlooks engine installed, but I'm just not sure because, well, it's not working.

---

### Post by GStubbs43 on 2006-10-04
That's just a GNOME Bug, kinda. I don't think you can make it full transparent without third-partty apps (ask someone else ;) ) KDE (Kubuntu) Can do that though.

---

### Post by bvc on 2006-10-04
you can use the pixbuf engine
[http://gnomethemes.org/forum/index.php?topic=67.0](http://gnomethemes.org/forum/index.php?topic=67.0)

---

### Post by pak33m on 2006-10-05
Thank you GStubbs43 & bvc.

I got a reply form the author of the theme.  He suggested that:

the reason why it looks like that is, the background pixmap image used in the theme, and also the "fake transparency" of gnome-panel.

You have some options:

* do not use panel transparency
* use xgl and compiz, use real transparency
* remove the line starting with "bg_pixmap" in gtkrc file and use the theme without brushed metal background.
* wait for an unpixmapped new version :)

Well, I commented out the bg_pixmap line in the gtkrc file, executed a killall gnome-panel & VIOLA - I have a full transparent panel with the theme!

Thanks again.

---

