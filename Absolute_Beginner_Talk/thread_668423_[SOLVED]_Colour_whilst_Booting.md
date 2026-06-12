---
title: "[SOLVED] Colour whilst Booting"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Matuku on 2008-01-15
This is mainly an aesthetic thing; after I've got to the logon screen and I've entered my username and password and I hit enter, the background whilst loading the desktop is the original Ubuntu colour (that nice pale cream-brown) [there also used to be a splash screen telling me what was being loaded but either that disappeared in Gutsy or I've somehow removed it]. What I'm wondering is how can I change this colour? My theme on Ubuntu is a nice dark blue and I've got everything focused around this (logon screen, theme, background) but this colour whilst loading kinda ruins it. As I said, its purely an aesthetics but we all want our Ubuntu to look beautiful right?

---

### Post by philinux on 2008-01-15
System>Admin>Login Window

Click local tab - down there is background colour. Change this to your choice

---

### Post by Matuku on 2008-01-15
Nope, tried that before; it displays that colour for a split second both before and after loading the logon screen but then switches to the default "creamy" colour.

---

### Post by Matuku on 2008-01-16
*Bump*

---

### Post by philinux on 2008-01-16
These are my settings for you to compare yours. I don't get no cream at all. you may have to ctrl backspace and login again for any changes to take effect.

---

### Post by Paul820 on 2008-01-16
If it won't change by using the settings in the login manager, take a look at this link where you can put in the code for the colour yourself: [http://www.ubuntugeek.com/how-to-change-the-background-color-of-your-screen-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-change-the-background-color-of-your-screen-in-ubuntu.html")

---

### Post by ByteJuggler on 2008-01-16
Also, note there's a package called "gnome-art" which allows installing/skinning/theming various parts of the Gnome desktop, including (unless I'm mistaken) the logon manager.

Install it with Synaptic as usual, or from the command line (as usual) with:

```
sudo apt-get install gnome-art
```

A new shortcut is created under one of the administration menu's.

---

### Post by Joeb454 on 2008-01-16
I'd prefer it to tell me what it was loading if I'm honest.

---

### Post by Matuku on 2008-01-16
> **Paul820 said:**
> If it won't change by using the settings in the login manager, take a look at this link where you can put in the code for the colour yourself: [http://www.ubuntugeek.com/how-to-change-the-background-color-of-your-screen-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-change-the-background-color-of-your-screen-in-ubuntu.html")

Thanks I tried that and put them both to #000000 (black) but it's still happening; very odd. Here's a screenshot of my login manager:

---

### Post by Matuku on 2008-01-16
> **Joeb454 said:**
> I'd prefer it to tell me what it was loading if I'm honest.
I know; I'm not sure if I've disabled that somehow, or if it isn't in Gutsy at all (though I'm sure it was when I first installed it) or maybe if the fact that it won't show that is linked to that it won't change the background colour.

---

### Post by ingvildr on 2008-01-16
Change your background colour in System > Preferences > Appearance. I'm guessing its showing the colour behind your background image before its set.

Edit: Also to get back the splash screen go into gconf-editor and go into apps > gnome-session then set the show_splash_screen key.

---

### Post by Matuku on 2008-01-16
> **ingvildr said:**
> Change your background colour in System > Preferences > Appearance. I'm guessing its showing the colour behind your background image before its set.

Edit: Also to get back the splash screen go into gconf-editor and go into apps > gnome-session then set the show_splash_screen key.

Nope the background colour is set to black as well:

Will try the gconf-editor to see whats happening there.

EDIT: Ok, went into gconf-editor and got the splash screen back but it's still on the cream background.

---

### Post by Matuku on 2008-01-16
*Bump*

---

### Post by pimpaulogy on 2008-01-17
Here's what fixed it for me:
[http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2](http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2)

> FIXED!

edit this file:

```


sudo gedit /etc/gdm/PreSession/Default
```

and change "#dab082" to the color of your choice.

Hope this helps.

---

### Post by Matuku on 2008-01-18
Thank you! That's done the trick, it's working now. So what did that piece of code do?

---

