---
title: "Different fonts in LXDE/OpenBox"
date: 2010-12-01
forum: Art &amp; Design
---

### Post by kaemo on 2010-12-01
I recently started to use LXDE in my Ubuntu (previously I used Gnome; installed it using lubuntu-desktop meta-package). Had some issues but almost all of 'em are solved. Besides one - fonts. It seems that OpenBox is using different font rendering, or DPI maybe, that almost all GTK based apps (there are exception). It means that fonts in my Firefox look exactly the same way that they used to look in Gnome, but panel and window manager fonts, and as I mentioned, some apps have bigger or somehow differently rendered fonts. I use Arial font for all elements (beside console). Here are configs and screenshots:

[LIST]
[*]part of **$HOME/.config/openbox/lubuntu-rc.xml**
[/LIST]
```
    <font place="ActiveWindow">
      <name>Arial</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>Bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="InactiveWindow">
      <name>Arial</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>Bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuHeader">
      <name>Arial</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuItem">
      <name>Arial</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="OnScreenDisplay">
      <name>Arial</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>Bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
```
[LIST]
[*]OpenBox and interface settings (you can see difference in *Preferencje pulpitu*, panel, desktop icons desc. and other windows)__
[/LIST]
[http://img841.imageshack.us/img841/709/201012012216001280x1024.png](http://img841.imageshack.us/img841/709/201012012216001280x1024.png)

[]("http://img841.imageshack.us/i/201012012216001280x1024.png/")

---

### Post by dzon65 on 2010-12-02
Could you post a screenie please?
Edit: missed it.
Could be due to the openbox theme's rc, text-settings in windows. Shadow settings etc..

---

### Post by dzon65 on 2010-12-02
Just checked,don't see any difference in openbox arial and lxappearance arial.

---

