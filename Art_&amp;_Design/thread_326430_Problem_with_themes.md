---
title: "Problem with themes"
date: 2006-12-27
forum: Art &amp; Design
---

### Post by raze on 2006-12-27
Hi!

I recently upgraded from Ubuntu 6.06 to Ubuntu 6.10 with GNOME 2.16.1. One thing I am having some difficulties with, is the themes. Take a look at these screens:

[http://folk.uio.no/mariubo/screens]("http://folk.uio.no/mariubo/screens")

As you can see, the buttons doesn't look like they should. For the record, I don't use Compiz/Beryl.

Hope you can help me :)

Edit: They should look like this: [http://www.gnome-look.org/content/show.php?content=48553](http://www.gnome-look.org/content/show.php?content=48553) and [http://www.gnome-look.org/content/show.php?content=45987](http://www.gnome-look.org/content/show.php?content=45987)

---

### Post by ComplexNumber on 2006-12-27
i think the problem there is that you might not have the correct theme engine installed. you can see what engines you have installed in /usr/lib/gtk-2.0/2.10.0/engines. now go to gnome-look and install some more engines. the chances are, you won't have the following:
rezlooks
candido
experience
gflat
murrine



btw if you are compiling them from source, use "./configure --prefix=/usr"

---

### Post by raze on 2006-12-27
I have now installed all the engines you purposed, but I get the same result. All of the other "stock" themes work fine.

Edit: I finally got it to work. For other users who face the same problem, install gtk-engines-pixmap and gtk2-engines-pixbuf :)

---

### Post by ComplexNumber on 2006-12-28
> **raze said:**
> I have now installed all the engines you purposed, but I get the same result. All of the other "stock" themes work fine.

Edit: I finally got it to work. For other users who face the same problem, install gtk-engines-pixmap and gtk2-engines-pixbuf :)
well, i knew it was something that was missing from the engines. when themes don't look as expected, its usually because its using the default engine instead of the one thats intended for it. because i'm not familiar with those themes that you've shown, i'm not aware of which engine they use, so thats why i suggested that you install them all.
btw pixmap is one of the engines.

---

