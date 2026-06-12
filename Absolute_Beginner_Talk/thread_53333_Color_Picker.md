---
title: "Color Picker?"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by heatheranne on 2005-07-31
I am new to Linux, been using it about a week.  I am using Ubuntu and KDE.  Now that that's out of the way, here is my question.  In the Synaptic Package Manager, I searched for color picker and it said the kdegraphics package was installed.  So I searched for kcoloredit but cannot locate it anywhere in the K menu.  I checked under graphics and utilities and every other category.  Does anyone know where I might locate kcolorpicker if it is indeed installed?

Also, is there a better color picker?

Thanks in advance for any help.   ](*,)

---

### Post by SGC on 2005-07-31
**I have both KColorChooser and KColorEdit under:**
Kmenu -> Graphics -> More Applications

**If you didn't find them there, then create a shortcut by:**
- Right-click on the Kmenu and choose "Menu Editor" 
- Click on the "Graphics" folder and then hit "New item" button from the toolbar
- Name you shortcut KColorChooser
- In the right panel enter **kcolorchooser** in "Command" field (All in lower case)
- Click on the Icon and choose an appropriate one.
Repeat the same thing for KColorEdit
[B]
Alternatively, you can install debian-menu which will show you all the installed programs in your system, in the terminal run the following command:[/B]
sudo apt-get install menu menu-xdg

**Log out and then log in and you will find both KColorChooser and KColorEdit under:**
kmenu -> debian -> Apps -> Graphics

---

### Post by KingCharles on 2006-05-04
Hi there. I was wondering wether there was a similar application for Gnome?

i just dun' want to install extra KDE libs that only a color picker will get to use...  just trying to keep my system clean, if you know what I mean ;)

<--Edited-->

Oh... nevermind!  Just found Gcolor2.
Small and functional. Simply amazing.

---

### Post by azulcm on 2006-12-13
I'm new in Ubuntu. KColorChooser works fine for me. However, in Suse there is a color picker kicker applet. 

What package do I need to install to get the color picker applet?

Thanks.

---

### Post by muep on 2006-12-13
I don't know what the KDE color apps are like, but for Gnome there is Agave, which lets you select a color and find some matching colors for it.

---

### Post by fdoving on 2007-05-18
> **azulcm said:**
> I'm new in Ubuntu. KColorChooser works fine for me. However, in Suse there is a color picker kicker applet. 

What package do I need to install to get the color picker applet?

Thanks.

You need the 'kicker-applets' package.

- fdoving

---

### Post by azulcm on 2007-05-30
> **fdoving said:**
> You need the 'kicker-applets' package.

- fdoving

Thank you fdoving, it works great :-)

---

