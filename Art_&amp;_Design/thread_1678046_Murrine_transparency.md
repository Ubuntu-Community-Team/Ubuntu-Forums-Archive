---
title: "Murrine transparency"
date: 2011-01-29
forum: Art &amp; Design
---

### Post by blchinezu on 2011-01-29
Hi. 
I'd like to make the icons background zone of the nautilus file browser transparent (This would obviously apply to other applications too).
I currently use a custom build of the murrine engine (gtk2-engines-murrine-0.98.1.1 with modified defines for opacity in support.h) but I couldn't figure where could this be in the source code.
I've attached a screenshot that hopefully will help in understanding the ideea. In the left side is the normal murrine nautilus window and in the right side is the wanted murrine nautilus window (In the screenshot I used compiz opacity plugin to get that look but that makes the entire window more transparent and I don't want that. Only the black background should be more transparent).

If anyone has any ideea if this can be done please reply.
Thank you.

---

### Post by jwalker on 2011-02-01
omfg

i can't help you but could you please point me to somewhere where i can make my nautilus look like that, all fat borders and transcperent and what not? Is that an emerald theme or am I stuck in the past?

Those widgets are awesome too what are they? Are they transcperent too are have you modded this to death?

I'm jealous

---

### Post by blchinezu on 2011-02-02
I hope this helps :)

What I use:
> - darkness gtk2 (rgba true) theme made by adamantis and modified by me to have breadcrumbs.
- darkness emerald theme also customized
- compiz with blur plugin activated
- nautilus elementary instead of the default nautilus
- NowPlaying screenlet in the top-right corner customized also
- top and bottom things: awn (avant window navigator) the trunk version not the stable (one with custom theme also)Links:
> [http://gnome-look.org/content/show.php?content=124548](http://gnome-look.org/content/show.php?content=124548)
Darkness GTK2 rgba true, Emerald, Installation Instructions etc
(make sure you read my comments from the first comments page about rgba as it will solve some problems with the rgba module - my username is brucelee)

[http://gnome-look.org/content/show.php?content=137928](http://gnome-look.org/content/show.php?content=137928)
Darkness GTK2 theme rgba true with nautilus breadcrumbs modified by me

[http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html](http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html)
Nautilus elementary installation

[http://gnome-look.org/content/show.php?content=136480](http://gnome-look.org/content/show.php?content=136480)
Now Playing screenlet modified by me

[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)
AWN trunk installation guide


---

### Post by stanca on 2011-02-02
Here are the deb pack modified and compiled by me with 30% transparency instead of 90% default: 
 [http://dl.dropbox.com/u/10704281/gtk2-engines-murrine_0.98.1.1-1_amd64.deb](http://dl.dropbox.com/u/10704281/gtk2-engines-murrine_0.98.1.1-1_amd64.deb) 
 [http://dl.dropbox.com/u/10704281/Nautilus-elementary%20bzr%20branch%20installer.sh](http://dl.dropbox.com/u/10704281/Nautilus-elementary%20bzr%20branch%20installer.sh)

---

### Post by blchinezu on 2011-02-03
I never tried it at 30% but I'll check it out. (I'll have to compile it myself as I have a 32bit OS) In my screenshot it has 70% opacity.
Anyway... Any ideas about the thing I asked?

---

