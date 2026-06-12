---
title: "PowerMac G4 AGP resolution issues"
date: 2008-07-04
forum: Apple Hardware Users
---

### Post by inspiratron on 2008-07-04
hello all,

i haven't used ubuntu in a long time, and i recently installed the 8.04.1 PowerPC port on a PowerMac G4.  However, it won't let me change my resolution above 800x600, so i can't view some preference panes' buttons.  anyone know how to fix this?  i know my monitor can do 1280x1024 at 60hz...

thanks
inspiratron

---

### Post by oswaldkelso on 2008-07-05
I'm not sure which version of xorg is in 8.04 but if its 7.3 this may help

[http://forums.debian.net/viewtopic.php?t=26577](http://forums.debian.net/viewtopic.php?t=26577)

---

### Post by stream303 on 2008-07-05
You'll have to manually edit your /etc/X11/xorg.conf file with the proper video driver, resolution, and possibly disable glx/dri.  Search the faqs and threads relevant to your model.

Alternatively, you might be able to do it manually by reverting to the "old school" display utility in Gnome.

System > Preferences > Main Menu

Under MENU on the left-hand pane, click on OTHER.  In the right hand pane, click on Screens and Graphics.

Now, in Applications > Other

You should be able to pull up the Screens And Graphics utility - this one should allow you to actually choose your video card and resolution the old-fashioned way. :)  This utility is getting deprecated, so you may want to try your hand at manually editing xorg.conf.

---

### Post by avtolle on 2008-07-05
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) for some general information on /etc/X11/xorg.conf in 8.04, and illustrations of manually editing the file.

BTW, if you want to go to the "old school" utility directly, from the CLI```
gksudo displayconfig-gtk
```which is easier to get to for many as opposed to the editing of the menus as set out in stream303's post. Good luck, however you decide to go.

---

