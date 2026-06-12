---
title: "Can I change the login background image?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by SnowPunk98 on 2007-02-05
How can I change the background image for the login from the human theme Ubuntu deal to something else I want?

---

### Post by ComplexNumber on 2007-02-05
> **SnowPunk98 said:**
> How can I change the background image for the login from the human theme Ubuntu deal to something else I want?
just install a new theme from gnome-look(ie GDM themes). the background is provided in the theme. what you can do is to change the background, but keep the name exactly the same (otherwise you will have to change the name of the wallpaper that the theme points to in the xml file within the theme). if you want the same login widget but just want to change the wallpaper, then just go to the current theme in /usr/share/gdm/themes and change the wallpaper (ie delete it and put another one in its place, but with the same name and file extension).

---

### Post by Mba7eth on 2007-02-05
Come'on :-$ ... you could've you the search in this forum ... or just google it ... 

Anyhow this is a like to that .... the login screen is usually called GDM ( don't ask me why ?! ) 

[Check this out]("http://art.gnome.org/themes/gdm_greeter/")
you'll find alot there ... 
And sorry for what i said at the begning :) PIECE):P

---

### Post by flehnerz on 2007-12-18
> **ComplexNumber said:**
> just install a new theme from gnome-look(ie GDM themes). the background is provided in the theme. what you can do is to change the background, but keep the name exactly the same (otherwise you will have to change the name of the wallpaper that the theme points to in the xml file within the theme). if you want the same login widget but just want to change the wallpaper, then just go to the current theme in /usr/share/gdm/themes and change the wallpaper (ie delete it and put another one in its place, but with the same name and file extension).

How how in the hell do you modify the files in these folders when you're not root? HOw does one gain root access to these folders?

---

### Post by Humph on 2007-12-18
If you open a terminal window (Applications -> Accessories -> Terminal) and change to the theme you want to alter (e.g. Human)

```
cd /usr/share/gdm/themes/Human
```You can then, say, edit the existing background file in GIMP:

```
sudo gedit background.png
```or you could create a background from scratch and save it in your Pictures folder, then copy it to the theme directory:

```
sudo cp /home/humph/Pictures/mybackground.png /usr/share/gdm/themes/Human
```You can then edit the Human.xml file to point at your new background image:

```
sudo gedit Human.xml
```and change the section

```
  <!-- background -->
  <item type="pixmap">
    <normal file="**mybackground.png**"/>
    <pos y="0" x="0" width="100%" height="100%"/>
  </item>
```to point at your desired image.

Hope this is of some help!

---

### Post by macogw on 2007-12-18
Why are you guys doing this the hard way???  Bah!

Just download the .tar.gz from gnome-look.org then drag and drop it into the choosing area on System > Administration > Login Window > Local

> the login screen is usually called GDM ( don't ask me why ?! ) 
GNOME Display Manager

---

### Post by Humph on 2007-12-18
> **macogw said:**
> Why are you guys doing this the hard way???  Bah!
And I thought that editing the image/xml file was *easy*!

> **macogw said:**
> Just download the .tar.gz from gnome-look.org then drag and drop it into the choosing area on System > Administration > Login Window > Local

Ooh funky! Never knew you could do that!

*goes to play with newly downloaded gdm theme*

---

