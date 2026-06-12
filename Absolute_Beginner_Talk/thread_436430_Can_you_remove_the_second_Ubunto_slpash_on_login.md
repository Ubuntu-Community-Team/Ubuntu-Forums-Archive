---
title: "Can you remove the second Ubunto slpash on login?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-07
The splash screen that shows that it is loading Nautilus and other programs?  Doesn't match my desktop at all.

Thanks all!

---

### Post by TheRingmaster on 2007-05-07
something [here]("http://gnome-look.org/index.php?xcontentmode=160") may help. Someone else will have to explain how to actually do it.

---

### Post by gohanssjn on 2007-05-07
Ah, but those seem to be Grub splash screens.  I wish I could take a picture of what I mean, but it appears after I put in my user name and password.  Directly after actually.

---

### Post by kpel on 2007-05-07
What about a way to simply change the color, or is it a set image file?  I dislike the standard Ubuntu color theme so I've changed everything else and that little splash screen has been bugging me too.

---

### Post by gohanssjn on 2007-05-07
Yeah, even color change would be great.

---

### Post by Tundro Walker on 2007-05-07
**(Start) > System > Preferences > Splash Screen**

That should open up a GUI to "Install" splash screens...IE: surf for pictures to use.

EDIT: You can also use Synaptic to install some splash screens, then use the "Install" to point to them, which should totally change how the image and the icons display when the GDM is loading up.

Also, try...

**(Start) > System > Administration > Login Window**

That'll bring up a GUI with tabs that lets you setup auto-login and other things, including how the login screen looks.  Looking on the "Local" tab, you can have all kinds of fun by changing the login screen splash image, the icon image that shows up in the login box, the background color of your screen, etc.

Hope this helps!

---

### Post by C-A on 2007-05-07
here is one option

install GNOME Splash Screen Manager

then go to: system > preferences > splash screen 

here you can disable the splash screen or change it

EDIT: didn't realize this was answered when I submitted my reply!

---

### Post by LuisGMarine on 2007-05-07
What you are referring to is called the gnome Splash Screen.  

Here is a quick and dirty guide on how to change your splash screens.

=============================================

First go ahead and download the gnome-splashscreen-manager, type this into a terminal:
```
sudo apt-get install  gnome-splashscreen-manager
```

This installs the program, which you will find under System > Preferences > Splash Screen.

This program is going to give you a nice and simple GUI manager for you splash screens.


=============================================

**Installing and activating splash screens**

The first thing you need to do is download the splash screen you want to use.  I would recommend going over to [GNOME-Look]("http://www.gnome-look.org/") and clicking on ' Splash Screens ' in the navigation menu.  From there download the Splash Screen of your choice, and download the picture to a folder you know is going to exist and not get deleted.

By this I mean creating a custom folder somewhere on your computer where you will store these type of things, and they will not get deleted.  For me I have a folder under '/home/USERNAME/stuff' 
[I]
Note: Of course USERNAME  is replaced by my actual user name.  You can do what ever you want, just make sure you save it to a place where its easily accessed! [/I]

Open up the program above by going to System > Preferences > Splash Screen, once that is up, hit the Install button at the bottom right-hand corner, and locate your splash screen hit the ' open ' key and you should now see it under the " Installed Splash Screens. "

To activate the splash screen, you can click on the splash screen you want on the list once, and click the 'Activate Button' on the bottom left-hand side, or you can just double-click it

To make sure that is activated, you should see something next to the name of the splash screen that says ( Activated )

===========================================

Changing the default color of the desktop during the splash screen.  

This answers a common question, when ubuntu splash screen is playing, there is usually a solid color desktop behind it, by default I think its orange or brown, which has to do with Ubuntu ... Obviously.

To change this is very simple.  Head over to System > Administration> Login Window.

Once the Login Window Preferences is up, click on the 'Local' tab, and towards the bottom there is an option that says " Background Color " , change that to whatever you want and that color is going to be the color of the background when the splash screen is loading.

Hope this helps you guys, 

Good Luck

---

### Post by gohanssjn on 2007-05-07
Thanks!  Got it removed :D

---

### Post by kpel on 2007-05-08
Excellent, thanks.  I didn't realize there was a splash screen manager available.

---

### Post by mcduck on 2007-05-08
It can also be changed or disabled through gconf-editor, just browse to apps/gnome-session/options.. So no need to install any extra applications for such a small task ;)

edit: If you wish to use your own image, put it in /usr/share/pixmaps/splash

---

### Post by ramjet_1953 on 2007-05-08
Even better is [COLOR="Blue"]gnome_art[/COLOR]

Just download it using synaptic or by typing in a terminal:

[COLOR="Red"]sudo apt-get install gnome-art[/COLOR]

It has heaps more options and includes a huge selection of eye candy for your screen.

Regards,
Roger :cool:

---

