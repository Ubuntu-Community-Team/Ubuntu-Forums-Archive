---
title: "Basic theme installation question"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by dschmier on 2007-05-16
I have tried many times to install various themes either from gnome-look or elsewhere.  As I understand it, there are two types of themes (that are relevant for me) -- Metacity and GTK.  As far as I know one of those controls how windows look in general, and one specifically draws the window borders.  However, the "Themes" manager in Ubuntu does not seem to draw a distinction between the two, and hence, I have never been able to get a theme to change anything other than the window borders (and the icons, etc).  I really want to get the Ubuntu Studio theme working, though, but after installing all that has changed is the window borders and the panels.  The text color in the panels did not change and the color of the menus and of the buttons for minimized programs in the panel did not change.  I figured out how to change the text color manually, so that's fine.  But I want my desktop to look like the one in the screenshots at the Ubuntu Studio website and that means having the *insides* of the windows be some sort of dark gray, rather than just changing the window borders.  How to do I get the theme to change these to the appropriate color (some sort of dark gray)?  Any help would be greatly appreciated.

---

### Post by Gmbrdilos on 2007-05-16
there is a probability that the package itself does not include much and those people are using combinations of other themes that they have.

---

### Post by dschmier on 2007-05-16
I don't think that's it, because I've seen other tutorials for installing the Ubuntu Studio theme (for example this: [http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/]("http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/") and that also has a screenshot with the workspace switcher, etc, in gray.  I guess my question is just how to install a GTK theme in general, as simply setting the theme in the "Theme" utility under Preferences does not seem to do it.

---

### Post by esoterica on 2007-05-16
System >> Preferences >> Theme

Then select the Customize button, this will give you the options to change your window backgrounds, font colors and everything else. Your current theme will be in the list, so just customize that one then save this with a new name of your choice.

My own project for the night is to change the look of my own system, I'm going to try these instructions out...

[http://www.linuxplanet.com/linuxplanet/tutorials/6223/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6223/1/)

I don't particularly want an OS X look alike, but anything is better than the very outdated look of standard Linux.

---

### Post by Kobalt on 2007-05-16
To get the full UbuntuStudio theme, open up a Terminal and run these three command lines (these will add & activate the UbuntuStudio repositories and install the theme) : ```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install ubuntustudio-look
```
After this the full look will be available from System > Pref. > Themes.

Enjoy :)

---

