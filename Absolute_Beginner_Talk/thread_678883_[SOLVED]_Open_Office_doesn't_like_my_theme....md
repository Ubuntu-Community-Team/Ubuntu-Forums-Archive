---
title: "[SOLVED] Open Office doesn't like my theme..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by doorknob60 on 2008-01-26
When ever I use open office, the icons and pictures don't show up.
[[IMG]http://img222.imageshack.us/img222/2687/openofficeproblemshd1.th.png[/IMG]](http://img222.imageshack.us/my.php?image=openofficeproblemshd1.png)

The slide shown is supposed to have a background picture (and does when I use the Human theme or even MS Power Point) Well, what I'm really asking is if there is either a way to make Open Office to like my theme, or if I can tell it to use a different theme just for that program (I have a similar looking theme that work fine with it).

---

### Post by doorknob60 on 2008-01-26
Help please I have a Power Point I have to do for school and it's been a major pain using M$ Office -.- (although I figured out I can switch themes but still...I want it to use a different theme just for Open Office)

---

### Post by doorknob60 on 2008-01-26
bump......

---

### Post by phyrewall on 2008-01-26
Here are some fixes for common problems using dark Gnome themes.

**Firefox**
If web forms and controls appear dark and unreadable you need to add the provided file "userContent.css" to the "chrome/" subfolder in your Firefox profile. It contains settings to get the default colors back. 
Install the theme with Gnome Theme Manager and type the following in a terminal:

 mv $HOME/.themes/Divinorum/userContent.css $HOME/.mozilla/firefox/*.default/chrome/

Note that the place of the chrome directory may vary on different Linux distributions.


**Pidgin**
In gaim/pidgin chat window there is black text on black background...
To fix this create a file named "gtkrc-2.0" in .purple dir in your home and put the following in it:

style "Custom"
{
base[NORMAL] = "#292B29"
}
class "GtkWidget" style "Custom"


**Open Office 2**
To get a white document background color instead of black, go to:

Tools > Options > OpenOffice.org > Appearance > Custom Colors > Document background

For dark themes Open Office 2 uses a high contrast icon theme (due to automatic icon settings). If you don't like this, do the following:

1. Open "Tools -> Options dialog -> OpenOffice.org -> View"

2. Change the icon theme from automatic/null to a different one.

---

### Post by doorknob60 on 2008-01-26
I know how to change the background color in Open Office but the problems is NONE of the pictures or icons show up...at all. BUT they show up in my other Gnome themes and I want to somehow tell it that whenever I use Open Office to use a different theme. Thanks for the Firefox and Pidgin tips though :)

---

### Post by mcduck on 2008-01-26
> **doorknob60 said:**
> I know how to change the background color in Open Office but the problems is NONE of the pictures or icons show up...at all. BUT they show up in my other Gnome themes and I want to somehow tell it that whenever I use Open Office to use a different theme. Thanks for the Firefox and Pidgin tips though :)

JUst follow the instructions phyrewall gave about changing icons in OO. That will work (I'm using dark GTK2-theme myself and that is exactly how I got the icons to work with the theme).

---

### Post by doorknob60 on 2008-01-26
[[IMG]http://img251.imageshack.us/img251/5262/problem2zg7.th.png[/IMG]](http://img251.imageshack.us/my.php?image=problem2zg7.png)

As you can see, it fixed half the problem, but my pictures still won't show up -.- Kind of a big problem when you're doing a Power Point with pictures of Crater Lake and you can't see them :P

EDIT: i found a slightly ugly solution... by removing the package openoffice.org-gtk, it makes it not as integrated with gnome (it looks like my KDE theme now for some reason) but it works. If someone has a better solution then I'd be happy to hear it though :) Also now compiz doesn't wokr on the menus :( That even works in Wine!! Oh well...

---

### Post by OZFive on 2008-01-27
I had that problem and then realized that Xubuntu had not installed the icon themes of OpenOffice.  Go to the Synaptic Package Manager and search for OpenOffice and look down the list till you find the icon themes.  Install them and then try again!  The icon themes should be there ready to use.

---

### Post by doorknob60 on 2008-01-27
I had the icon themes already, but apperantly it wasn't using any so that doesn't help much. I had to tweak my Compiz settings or it would sometimes start in full screen, which was really weird but everything's good now. (I wondered why OOo looked funny on my old computer when it had Xubuntu though...)

---

