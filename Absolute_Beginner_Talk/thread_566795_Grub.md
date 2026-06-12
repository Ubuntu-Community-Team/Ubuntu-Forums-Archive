---
title: "Grub"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-10-03
Ok, I read somewhere *and I can't find the thread now* that the default for ubuntu is to have the background for Grub turned off... Does anyone know how to change this?

---

### Post by upbeat.linux on 2007-10-04
You'll need to create a default image and edit the menu.lst file to add a link to the image:

```
splashimage=/path/to/image
```

A few good tutorials are listed here:

[http://osresources.com/1_5_en.html]("http://osresources.com/1_5_en.html")

[http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB]("http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB")

---

### Post by eph1973 on 2007-10-04
There's some splashimages available through apt-get:

```
sudo apt-get install grub-splashimages
```

This will install several *.xpm.gz files in the directory /boot/grub/splashimages.

If you create your own xpm for the GRUB splashimage, remember the sizing and number of colors restrictions.

Also pay attention to the bit about specifying the partition that your root directory is in (that hd(0,1) or whatever it ends up being).  If you don't know which partition your root directory is on, enter the following:

```
cat /boot/grub/menu.lst | grep "^title\|^root.*hd"
```

You will see several lines, look at the ones that list your most recent kernel, and directly below those lines, it should say something like
```

root              (hd0,3)

```
or something like that.  Whatever it says in parenthesis is what you should add to the beginning of the splashimage (hd(whatever))/boot/grub/splashimages/(your favorite splash image).xpm line you need to add in the menu.lst file.

---

### Post by upbeat.linux on 2007-10-04
Thanks for the reminder about sizing and color restrictions eph1973. I tend to forget about that myself :P

---

