---
title: "make xfce look like gnome classic? (aka like sabayon 7)"
date: 2011-10-29
forum: Any Other OS
---

### Post by gyyug78fg87ogguiioioioioi on 2011-10-29
i installed sabayon 7 xfce version but i dident like it but i very mutch liked how the xfce config looks like the gnome classic like this:

[[IMG]http://img254.imageshack.us/img254/2177/screenshot1030201102101.th.jpg[/IMG]](http://imageshack.us/photo/my-images/254/screenshot1030201102101.jpg/)

i am talking about the two panels down and up, how could i possibly make crunchbang 10 xfce version look just like this? also make crunchbang behave like the classic xfce, with icons on the desktop etc, because it is actualy xfce inside openbox or something, after a fresh install..

if not, how could i do this with xubuntu atleast.?

---

### Post by Toz on 2011-10-29
> **gyyug78fg87ogguiioioioioi said:**
> if not, how could i do this with xubuntu atleast.?

Shouldn't be too difficult. There are 2 panels, top and bottom. To access the panel settings, right-click the appropriate panel, select Panel then Panel Preferences. (for xubuntu 11.10)

```
Top Panel
 Display Tab
  Orientation=Horizontal
  Lock Panel = checked
  Automatically show...=unchecked
  Measurement size = set as desired
  Measurement length = 100%
  Automatically increase length = checked
 Appearance Tab
  Alpha = 50 ?(set as desired for transparency effect)
 Items Tab (I'm guessing here based on image)
  Applications Menu item
  Quicklauncher item
  Expanding transparent separator
  Indicator plugin
  Workspace switcher item
  Clock item
  Notification area item

Bottom Panel
Display Tab
  Orientation=Horizontal
  Lock Panel = checked
  Automatically show...=unchecked
  Measurement size = set as desired
  Measurement length = 100%
  Automatically increase length = checked
 Appearance Tab
  Alpha = 100 (doesn't look like its transparent)
Items Tab (I'm guessing here based on image)
  Show Desktop item
  Window Buttons item
  Expanding transparent separator
  Trash applet
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-10-29
where do i add that code then?

---

### Post by 3Miro on 2011-10-29
The XFCE panels have pretty good graphical settings tools. Go to Applications -> Settings -> Settings Manager -> Panel and you should be able to adjust the size and position of the panel as well as the different applets.

I have attached my setup on Gentoo + XFCE (Sabayon is based on Gentoo, you should be able to get exactly the same) Other than the panel, you can get the Clearlooks theme, just install extra themes from the repository and the extra themes for xfwm4.

---

### Post by Toz on 2011-10-29
> **gyyug78fg87ogguiioioioioi said:**
> where do i add that code then?

It's not code but rather settings. As 3Miro indicates, you can either "Go to Applications -> Settings -> Settings Manager -> Panel" or just right-click the Panel then select Panel->Panel Preferences to access the graphical module to configure the panels.

---

### Post by Megaptera on 2011-10-30
Possibly this "How to...."  may be of interest?
[http://robinsrantsandraves.wordpress.com/2011/07/20/an-unity-inspired-xfce-dock-in-xubuntu-10-04/](http://robinsrantsandraves.wordpress.com/2011/07/20/an-unity-inspired-xfce-dock-in-xubuntu-10-04/)

---

### Post by Elfy on 2011-10-30
Thread moved to Other OS/Distro Talk.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-10-31
thanks

---

### Post by Testingte on 2012-01-23
[http://namakutux.blogspot.com/2011/11/how-to-make-xfce-looks-like-gnome-2.html](http://namakutux.blogspot.com/2011/11/how-to-make-xfce-looks-like-gnome-2.html)

Hope that helps! :D

---

### Post by mips on 2012-01-24
To enable desktop icons you will loose the right click desktop menu.

Go to Settings->Desktop->Menus Untick "Show application menu on dektop right click"
Go to Settings->Desktop->Icons->Icon type: "File/launcher icons.

Some other possible useful info,
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)
[http://www.omgubuntu.co.uk/2011/10/how-to-enable-ubuntus-global-menu-in-xubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/how-to-enable-ubuntus-global-menu-in-xubuntu-11-10/)

You should be able to do all the above things in Crunchbang as well.

---

