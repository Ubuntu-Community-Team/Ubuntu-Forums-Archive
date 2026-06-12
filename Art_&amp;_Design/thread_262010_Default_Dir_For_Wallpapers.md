---
title: "Default Dir For Wallpapers"
date: 2006-09-21
forum: Art &amp; Design
---

### Post by buzlink on 2006-09-21
What is the default loction for wallpapers to be stored?

Thanks!

---

### Post by mssever on 2006-09-21
Wallpapers are in /usr/share/wallpapers and /usr/share/backgrounds.

---

### Post by buzlink on 2006-09-21
> **mssever said:**
> Wallpapers are in /usr/share/wallpapers and /usr/share/backgrounds.

I am able to browse to that folder but can not copy files into the dir.  How can I get a wallpaper that I downloaded to my desktop into the dir?  Also there are wallpapers in the folder that do not show up in the wallpaper dialog box when I right click on the desktop.

Thanks!

---

### Post by arkangel on 2006-09-21
you cannot copy  because you dont have the right permisions  ,  in a linux (Unix) systems  your home is your place  you can read  erase or modify the data the way you want ,  outside your home dir (most probably located in /home/myuser)  only root or admins can modify 

you can  create in home a special folder like wallpapers(or whatever) and put them inside 

or use administrative  rights
for example 
in a console go where your wallpaper is and type 
# cd ~/Desktop
# sudo mv  mywallpaper.png /usr/share/wallpapers
and enter your pass(i am assuming that you were the first user when linux was installed  and you belong to  the admin group by default )

---

### Post by buzlink on 2006-09-21
> **arkangel said:**
> you cannot copy  because you dont have the right permisions  ,  in a linux (Unix) systems  your home is your place  you can read  erase or modify the data the way you want ,  outside your home dir (most probably located in /home/myuser)  only root or admins can modify 

you can  create in home a special folder like wallpapers(or whatever) and put them inside 

or use administrative  rights
for example 
in a console go where your wallpaper is and type 
# cd ~/Desktop
# sudo mv  mywallpaper.png /usr/share/wallpapers
and enter your pass(i am assuming that you were the first user when linux was installed  and you belong to  the admin group by default )

Got it, I knew I didn't have write permission but didn't know how to obtain it and copy things over!  Still allot of learning to be done.
Thanks!

---

### Post by HanZo on 2006-09-21
an other dirty yet easy trick is to execute the following in a terminal:
```
sudo nautilus
```
that starts nautilus in root mode... but be careful you could delete or move something important.

---

### Post by buzlink on 2006-09-21
> **HanZo said:**
> an other dirty yet easy trick is to execute the following in a terminal:
```
sudo nautilus
```
that starts nautilus in root mode... but be careful you could delete or move something important.

How long does root last doing it that away?
Thanks much easier, as I"m not good with the command line yet.

---

### Post by mssever on 2006-09-21
> **buzlink said:**
> How long does root last doing it that away?
Thanks much easier, as I"m not good with the command line yet.
Root lasts for as long as that Nautilus window is open. 

If you're just trying to set wallpapers, then you can go to System > Preferences > Desktop Background and click on the Add wallpaper button.

---

### Post by xmastree on 2006-09-23
> **HanZo said:**
> an other dirty yet easy trick is to execute the following in a terminal:
```
sudo nautilus
```
that starts nautilus in root mode... but be careful you could delete or move something important.

I find it useful to change the nautilus background to some violent mustard colour, to remind myself that I'm not in **my** nautilus, and I need to be careful.
:idea: 
You could even take it further, and make a tile which says ROOT and use that.

---

