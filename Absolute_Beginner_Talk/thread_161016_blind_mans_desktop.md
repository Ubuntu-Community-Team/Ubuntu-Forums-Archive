---
title: "blind mans desktop"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-04-16
Hi all

wonder if u can help me being that i now feel like i am back in computer kindergarten :) like everyone i know what i want to do and how to do it in windows but i want have decided to make the move to ubuntu. Now due to the crazy hardware set up on my laptop i am running the dapper version (i think that was rite) but here is the killa.

I am visually impaired and require the what to everyone else is a wacky desktop. is this easy to configure?

I want to be able to change the following (i knolw i shouldnt buut i am using the names as shown in windows as i dont know if they are called the same in ubuntu)

3d objects = basically the colour of the box = dark blue
window background ==  maroon/dark red
window text == yellow
menu text == white.

if it would be easier i can provide a screenshot of what i am after, I know to everyone apart from me or those with severe eye problems the above sounds horrible but it is the difference between being able to use my pc or not so it is REALLY important i am able to do this.

any help anyone can provide will be greatfully received.

cheers
niteblind

---

### Post by JoshHendo on 2006-04-16
For the BG, you should be able to go into the change background in:

System -> Preferences -> Desktop Background

Then select "No Wallpaper". Under desktop colours, select solid, and next to that you will be able to change what colour you want the BG to be.

As for the Window text and menu text, you will probably need to use a custom theme for that. I am no good when it comes to making themes, though I am sure that someone will be able to either tell you how or find a good theme to suit your needs.

-Josh

---

### Post by htinn on 2006-04-16
If you use KDE, you can simply change the colors using one of the kcontrol setting things. For GNOME, you'd need to find a specific theme at [http://www.gnome-look.org/](http://www.gnome-look.org/) or some place like that.

---

### Post by catlett on 2006-04-16
If you go into theme management you can change  the window border, the controls and the icons. You should be able to get the mix you want.
Go to the top of your desktop and click on "System". Scroll down one spot to "Preferences". A box slides out. Scroll down to "Themes". This will open up the "Theme Preference" window.  The theme your using will be highlighted. 
To change what you want click on "Theme Details". This will give you 3 options to work on. "Controls", which are the maximise, minimise buttons and scroll bar etc. "Window Border", which is the border around the window box. And Icons which is the icons of course.
Also in "Preferences is "Font" where you can change the font style. There is "Assistive Technolongy Support" but I don't know if your looking for a magnifier,screenreader or not.
That's about all I know. It should at least get you started. You might want to try the websites "GnomeArt" and GnomeLook" they have many themes, fonts etc for the Gnome desktop. Maybe someone has created a theme with the things you are looking for.

---

### Post by niteblind on 2006-04-16
thanks loads guys especially for the fast response will try these out now wish me luck 

niteblind

---

### Post by siminone on 2006-04-16
The Gnome highconstrast theme looks like the one you are after Niteblind. 

To get this takes a bit of work. 

Firstly install gtk2-engines-highconstrast from synaptic

Download gnome-accessibility themes from debian.org

[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgnome-themes%2Fgnome-accessibility-themes_2.8.2-3_all.deb&md5sum=c543bd8d41b09955efc69a5694835e97&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fg%2Fgnome-themes%2Fgnome-accessibility-themes_2.8.2-3_all.deb&md5sum=c543bd8d41b09955efc69a5694835e97&arch=all&type=main)

On the gnome terminal type in:

sudo dpkg -i gnome-accessibility-themes_2.8.2-3_all.deb


The gnome accessibility themes will be installed:

On the Ubuntu toolbar, click on system menu
Click on preferences
Click on Theme

---

### Post by siminone on 2006-04-16
for some reason, after installing gnome-accessiblity themes from debian package it is now avaialable in synaptic as default.

Is anybody else got the package?

---

### Post by Zeroangel on 2006-04-16
The High Contrast themes are available in the Dapper repositories, all you have to do is run this command in the terminal:
```
sudo apt-get install gnome-accessibility-themes
``` Then go into the theme manager from the list of theme presets.

Customize it to your liking and enjoy! :D

---

### Post by siminone on 2006-04-16
Hopefully gnome-accessibility themes will be in next release without need to install.

[https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/30107/+index](https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/30107/+index)

---

### Post by Henrik on 2006-04-25
"Hopefully gnome-accessibility themes will be in next release without need to install."

Indeed that will now be the case. We have decided to have one high contrast theme in by default and let the other ones be installable.

---

