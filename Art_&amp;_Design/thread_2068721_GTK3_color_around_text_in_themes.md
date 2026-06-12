---
title: "GTK3 color around text in themes"
date: 2012-10-09
forum: Art &amp; Design
---

### Post by digitaltracer on 2012-10-09
I edited some good themes available on net but I am not able to remove the color around texts in menus and buttons.

It works perfectly well in firefox,chrome,synaptic etc

Someone who is good in gtk3 please help

[IMG]http://i.imgur.com/Lv0I2.png

---

### Post by vasa1 on 2012-10-09
Could you put up two images illustrating only what you have and what you want to have? In other words, don't put up full-screen images because then it isn't clear what the focus should be on.
Also, specify the theme involved and the origin of the image and the distro. Some themes work well with one distro but look ugly with another.

---

### Post by digitaltracer on 2012-10-10
See the colour around menu items and buttons in below items.. I want to remove those colors. I am using Ubuntu 12.10 Quantal Beta 2 and I have used Macbuntu-Xii-gtk3-Theme [edited myself a bit] [[http://www.mediafire.com/?v07hyi66zzicqo1](http://www.mediafire.com/?v07hyi66zzicqo1) ]

What I have:

[http://i.imgur.com/LoYF2.png](http://i.imgur.com/LoYF2.png)

[http://i.imgur.com/P9JOp.png](http://i.imgur.com/P9JOp.png)

What I want to have

[http://i.imgur.com/hZ3QK.png](http://i.imgur.com/hZ3QK.png)  ( This is from same theme taken from Mozilla Firefox dialog)

---

### Post by vasa1 on 2012-10-10
> **digitaltracer said:**
> See the colour around menu items and buttons in below items.. I want to remove those colors. I am using Ubuntu 12.10 Quantal Beta 2 and I have used Macbuntu-Xii-gtk3-Theme [edited myself a bit]...
My guess is that the theme you're using relies on images to theme buttons. There are other themes that do the same using css (gradients, shadows, etc). If your theme is indeed using images, you'll have to edit the images after identifying which is which. They may have names like:

```
[02:09 PM] ~/.themes/DAY/gtk-2.0/images $ ls -l
total 304
...
-rw-r--r-- 1 vasa1 vasa1  210 Jul  5 23:42 arrow-up-combo.png
-rw-r--r-- 1 vasa1 vasa1  245 Jul  5 23:42 arrow-up-ins-combo.png
-rw-r--r-- 1 vasa1 vasa1  200 Jul  5 23:42 button-ins.png
-rw-r--r-- 1 vasa1 vasa1  214 Jul  5 23:42 button.png
-rw-r--r-- 1 vasa1 vasa1  211 Jul  5 23:42 button-pressed.png
-rw-r--r-- 1 vasa1 vasa1  288 Jul  5 23:42 button-sel.png
...
-rw-r--r-- 1 vasa1 vasa1  207 Jul  5 23:42 menu-arrow-up.png
-rw-r--r-- 1 vasa1 vasa1   90 Oct  9 09:26 menubar.png
-rw-r--r-- 1 vasa1 vasa1 1002 Oct  9 22:21 menuitem.png
-rw-r--r-- 1 vasa1 vasa1  117 Oct  9 23:13 notebook-bottom-gap.png
-rw-r--r-- 1 vasa1 vasa1  194 Jul  5 23:42 notebook-left-gap.png
-rw-r--r-- 1 vasa1 vasa1  869 Oct  9 23:09 notebook.png
-rw-r--r-- 1 vasa1 vasa1  193 Jul  5 23:42 notebook-right-gap.png
-rw-r--r-- 1 vasa1 vasa1 1028 Oct 10 08:59 notebook-tab-bottom-active.png
-rw-r--r-- 1 vasa1 vasa1  248 Oct 10 12:21 notebook-tab-bottom.png
-rw-r--r-- 1 vasa1 vasa1  254 Jul  5 23:42 notebook-tab-left-active.png
-rw-r--r-- 1 vasa1 vasa1  246 Oct  9 09:26 notebook-tab-left.png
-rw-r--r-- 1 vasa1 vasa1  254 Jul  5 23:42 notebook-tab-right-active.png
-rw-r--r-- 1 vasa1 vasa1  244 Oct  9 09:26 notebook-tab-right.png
-rw-r--r-- 1 vasa1 vasa1  905 Oct 10 09:13 notebook-tab-top-active.png
-rw-r--r-- 1 vasa1 vasa1  278 Jul  5 23:42 notebook-tab-top.png
-rw-r--r-- 1 vasa1 vasa1  857 Oct 10 12:24 notebook-top-gap.png
-rw-r--r-- 1 vasa1 vasa1   77 Oct  9 09:26 null.png
-rw-r--r-- 1 vasa1 vasa1 1265 Oct  9 06:01 panel-bg.png
-rw-r--r-- 1 vasa1 vasa1  627 Jul  5 23:42 panel-button-active.png
-rw-r--r-- 1 vasa1 vasa1  647 Jul  5 23:42 panel-button-hover.png
-rw-r--r-- 1 vasa1 vasa1   96 Jul  5 23:42 panel-button-inactive.png
...
-rw-r--r-- 1 vasa1 vasa1  993 Oct  9 17:29 toolbar.png
[02:09 PM] ~/.themes/DAY/gtk-2.0/images $ 

```

---

### Post by digitaltracer on 2012-10-10
Thanks vasa1, I could remove color around top Menubar text but still I am not able to remove this color for right click menu and  buttons .

Here is the picture of my current situation.. kindly help

---

### Post by vasa1 on 2012-10-11
> **digitaltracer said:**
> ... kindly help
I'm afraid I won't be of more help because my free time is taken up with tweaking the theme I'm currently using with Lubuntu 12.10. I hope someone else can suggest something for you.

---

### Post by digitaltracer on 2012-10-11
Hi,
Can you please tell me where do you specify colors and other things for right click menu. I am not able to find on net

Thank you in advance

---

