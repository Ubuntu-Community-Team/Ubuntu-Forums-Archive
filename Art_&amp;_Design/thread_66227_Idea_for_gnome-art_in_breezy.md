---
title: "Idea for gnome-art in breezy"
date: 2005-09-16
forum: Art &amp; Design
---

### Post by sinbad782 on 2005-09-16
I've just upgraded a couple of machines to the breezy badger preview release. Pretty much everything has carried over ok and I noticed that the gnome-art app has now become available in the Universe repositories. When it is installed this appears under System -> Preferences -> Art Manager.

It would be nice if this app was integrated with the official Ubuntu Art site - i.e. someone could create a patch to add some submenus for each category with the content from the Ubuntu Art site at [http://art.ubuntu.com/](http://art.ubuntu.com/)

---

### Post by Wolki on 2005-09-17
[QUOTE=sinbad782]I've just upgraded a couple of machines to the breezy badger preview release. Pretty much everything has carried over ok and I noticed that the gnome-art app has now become available in the Universe repositories. When it is installed this appears under System -> Preferences -> Art Manager.

It would be nice if this app was integrated with the official Ubuntu Art site - i.e. someone could create a patch to add some submenus for each category with the content from the Ubuntu Art site at [http://art.ubuntu.com/](http://art.ubuntu.com/)[/QUOTE]

Not exactly what you want, but I did take a quick look...
"
do "sudo gedit /usr/lib/ruby/1.8/gnome-art/config.rb". Comment out the line 
```
XML_File = "http://art.gnome.org/xml.php"
```
 and add a new line directly underneath it: 
```
XML_File = "http://art.ubuntu.com/xml.php"
```

Now Gnome-art will access the Ubuntu Art site. It seems like it won't display thumbnails, don't know why yet. Of course you can't access art.gnome.org with it anymore until you undo these changes... :-/ Maybe i'll get to take a closer look at the code, but I can't promise it.

It would probably be too late for inclusion in Breezy anyway, feature freeze is long past.

w.

---

### Post by UbuWu on 2005-09-18
[QUOTE=Wolki] It seems like it won't display thumbnails, don't know why yet. [/QUOTE]

Because [http://art.ubuntu.com/xml.php](http://art.ubuntu.com/xml.php) points to the wrong url's. It refers to art.gnome.org instead of art.ubuntu.com. I mailed some people asking to change that, so I hope it all works soon...

---

