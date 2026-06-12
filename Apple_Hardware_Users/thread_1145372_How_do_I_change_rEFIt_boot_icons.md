---
title: "How do I change rEFIt boot icons?"
date: 2009-05-01
forum: Apple Hardware Users
---

### Post by perpetualcacophany on 2009-05-01
Alright, so in my quest to keep customizing my computer, I have run across something I can't quite figure out. When the rEFIt menu comes up, it shows Tux and the Apple logo. What I would like to have is the Ubuntu logo instead of Tux. Does anyone know how to do this? I know where these logos are stored, but I'm not sure what I would have to do exactly to change them. I assume I would just replace them with a same-size file of the same name and type. I would try that, but they are in a .icns format and I am not exactly sure how to make/edit that picture format. Any help would be appreciated.

Thank You.

---

### Post by cyberdork33 on 2009-05-01
you can use "Icon Composer" which is part of the OS X Developer Tools.

---

### Post by rifak on 2009-08-10
make your icon in gimp (or whatever), make sure it is in 128x128 dimensions, and save it as a png. you can use this site then ([http://iconverticons.com/](http://iconverticons.com/) ) to convert it to a .icns file. make sure to download the apple icns file it gives you, save it wherever, and change he name to match what is in the /efi/refit/icons/ folder. so, you would have to convert two png files, then name them one to os_linux.icns and one to boot_linux.icns.

i just did this, and made up a quick set...nothing to crazy, but it adds a little. you can use that site to convert them to .icns, then rename them. hope this helps

---

