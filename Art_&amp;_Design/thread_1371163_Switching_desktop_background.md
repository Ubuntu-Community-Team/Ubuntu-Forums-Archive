---
title: "Switching desktop background"
date: 2010-01-03
forum: Art &amp; Design
---

### Post by TopGear on 2010-01-03
Hey,

In KDE you can automaticly switch you desktop background time to time. But is this possible to in Gnome? I am allready using drapes, but it is making my desktop awful! See picture.

So can somebody help me? I really hope so!

[[img]http://www.plaatjesupload.nl/bekijk/2010/01/01/1262361584-070.jpg[/img]](http://www.plaatjesupload.nl/bekijken/2235891.html)
[IMG]http://%3Ca%20href=http://www.plaatjesupload.nl/bekijken/2235891.html%20target=_blank%3E[img]http://www.plaatjesupload.nl/bekijk/2010/01/01/1262361584-070.jpg[/IMG]

---

### Post by .nedberg on 2010-01-03
```
sudo apt-get install wallpaper-tray
```

That was the best answer to a similar thread a couple of days ago...

---

### Post by John Bean on 2010-01-03
I ended up writing a simple script to meet my purpose. The essential information is that the image to use can be set using gconftool:
```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename someimagefile.jpg
```In the example "someimagefile.jpg" should be replaced by the actual image you want to use., and in the simplest case you could just set up a cron job to do the change.

---

