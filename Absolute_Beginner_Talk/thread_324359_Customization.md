---
title: "Customization"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by DeadSuperHero on 2006-12-23
Well, I've only just started with Ubuntu, so I'm still in the learning phase.
A few questions:
-Where can I download new themes for Ubuntu?
-How can I make my own themes?
-How do I install the themes?

---

### Post by riven0 on 2006-12-23
> **Mr. Psychopath said:**
> Well, I've only just started with Ubuntu, so I'm still in the learning phase.
A few questions:
-Where can I download new themes for Ubuntu?
-How can I make my own themes?
-How do I install the themes?

[Gnome-look]("http://www.gnome-look.org") is the way to go for new themes. Not sure about making your own, though. I think there is info on that site.

---

### Post by OldTimeTech on 2006-12-23
If you have .jpg's that you like and are on your hard drive, you can with the add button in change background screen, make a wallpaper out of a .jpg.

---

### Post by Greevous on 2006-12-23
I myself prefer Gnome-look, but [art.gnome.org]("http://art.gnome.org") also has themes, borders, icons, etc.

---

### Post by ostvarivanje on 2006-12-23
Is there anybody to explain me how can I install beryl and compiz themes?

---

### Post by DeadSuperHero on 2006-12-23
Thanks for the advice.
Now, how do I install them? There seems to be different kinds of themes.

---

### Post by Greevous on 2006-12-23
> **ostvarivanje said:**
> Is there anybody to explain me how can I install beryl and compiz themes?

Just simply download the file from the site, and import it in Emerald. Right-click the red diamond and choose Emerald Theme Manager, then add your theme there.

For other themes, save the package file, then go to System>Preferences>Theme and click Install Theme. Find your file, and Ubuntu will add your new theme to the list.

---

### Post by riven0 on 2006-12-23
> **Mr. Psychopath said:**
> Thanks for the advice.
Now, how do I install them? There seems to be different kinds of themes.

Just download the tar.gz file and drag them to your themes window, listed under System >> Preferences >> Themes

It should install automatically.

---

### Post by sindrum_murdnis on 2006-12-23
heres some cool visual stuff i like to use .

Find your art work you would like to use from here
   [www.gnome-look.org](www.gnome-look.org)
   art.gnome.org

installing new cursors
   sudo apt-get install gcursor

changing login splash
   sudo apt-get install gnome-splashscreen-manager

change login screen
   gksudo gdmsetup

you can find these under system>preferences>

all this works under edgy eft not sure about the others. hope this helps

---

### Post by ostvarivanje on 2006-12-23
Thank you both, [COLOR="Red"]riven0 [/COLOR]and [COLOR="Red"]sindrum_murdnis[/COLOR] for your help. 
Now it's clear to me about emerald and metacity themes. But, I'm wondering if I can install in the metacity way and compiz themes.
I found in gnome-look gtk1.x and gtk2.x themes. Whats is the difference between them? What is better?
Thank you
Marry Christmas to all of you!8)

---

### Post by Ptero-4 on 2006-12-23
gtk1 themes are for apps built in gtk 1 (an old version of gtk used in gnome 1.x), you only need those if you happen to have gtk1 apps (there's no such old apps in the default install of ubuntu) and gtk2 themes are for the apps built for gtk2 (pretty much all the apps that come with the gnome version in ubuntu).

---

### Post by jem7v on 2006-12-23
To install Compiz or Beryl themes you first need to install Compiz or Beryl. They're composite window managers, so they take a little bit of fussing with to get working sometimes. Here's a page about what they vaguely are and how to install them.

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Folks are right about GTK1 vs 2. 1 is pretty much uneccesary at this point if you're running a current Ubuntu install.

---

### Post by ostvarivanje on 2006-12-23
Thank you for your interest and sorry for my bad english. I have installed both beryl and compiz, but only use beryl. I think (personally for me) that have better effects. 
After all these, I understand that better is gtk2 than 1 and of course beryl (emerald) themes. 
Something else now: can't I add more screensavers? Only these which have ubuntu when you install? And how can I set up the picture folder to see like screensaver? I must add in any folder fotos?
Thank you

---

### Post by crimesaucer on 2007-03-06
I'm not sure how the gtkrc is written in clearlooks and other gnome themes, but if you want to take a look at how easy a gtkrc in xubuntu (xfce-engines) is, then check out my how to that I wrote for modifying your default themes, to match the colors you want as well as making your buttons and scroll bars and drop down menus different.

This is my "How To" that I wrote. It's actually more of a list of where certain things go for the gtkrc using xfce-engines, kind of like a cheat sheet for gtkrc settings: [http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)


This is the easy way to start this if you are a beginner like I am: [http://ubuntuforums.org/showthread.php?t=371110](http://ubuntuforums.org/showthread.php?t=371110)

I also believe you must make sure you have the package from Synaptic called: gtk2-engines-xfce installed so my gtkcs work.

---

