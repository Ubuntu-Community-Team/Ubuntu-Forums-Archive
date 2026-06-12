---
title: "Gnucash - where is it?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by mkaareng on 2005-12-05
I've installed GnuCash through Synaptic, but where did it go? How do I find the program?

-Martin

---

### Post by carlosqueso on 2005-12-05
You should just be able to go into a terminal and type gnucash (I don't know...I'm at work and can't test it).  If that works, just create a launcher for the command gnucash.  If that doesn't work...come back in a few hours and I'll try to figure something out when I have access to my ubuntufied home comp.

---

### Post by 5-HT on 2005-12-05
*EDIT: just noticed carlosqueso got to this first...

Hi, I'm not familiar with Gnucash, but usually if the program is put in your $PATH when installed you can simply type in the name in a terminal to run it

```
 gnucash 
```

Also, if you want to make a launcher for it, or to add it to a panel, you can track down the path of the executable. The "which" command should do the trick nicely.

In this case try: ```
 which gnucash 
```

Then simply create a launcher, or add a new entry in Smeg (Applications Menu Editor) corresponding to the program.

Hope that helps.

---

### Post by popeye on 2005-12-06
Try this:

2. 	How do I install an accounting application (GnuCash)?
	
   1.      Make sure the universe repository is enabled. (See How do I add Universe and Multiverse?)
   2.      Install the gnucash package with Synaptic (See How do I use Synaptic to install packages?)

      Gnome Desktop Environment (universe) > gnucash

   3.      Remove some unnecessary directories and files.

        ```
sudo rm -fr /usr/share/gnome/apps/Applications/
```

   4.      Start a new desktop configuration file in the /usr/share/applications directory.

        ```
sudo gedit /usr/share/applications/GnuCash.desktop
```

      A blank file called GnuCash.desktop opens in gedit.

   5.      Add the following lines to the new file.

> [Desktop Entry]
Name=GnuCash
Comment=GnuCash Personal Finance
Exec=gnucash
Icon=/usr/share/pixmaps/gnucash/gnucash-icon.png
Terminal=false
Type=Application
Categories=Application;Office;
							

   6.      Save the file and close gedit. (See sample/GnuCash.desktop_gnucash for an example.)
   7.      To open GnuCash, choose Applications->Office->GnuCash.


[http://help.ubuntu.com/starterguide/...html#id2527799](http://help.ubuntu.com/starterguide/...html#id2527799)


Suc6

---

