---
title: "Dislike the purple and orange startup?"
date: 2010-10-10
forum: Art &amp; Design
---

### Post by peakpc on 2010-10-10
I had to find a way to change the purple and orange stuff at boot up, no offence but I just don't like the combo.  Themes are easy enough after logging but, changing the Plymouth boot colors and GDM screens took a little more doing...

Here is what I ended up doing:

For Plymouth, I enter "gksu gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script" in terminal then drill down to "Window.SetBackgroundTopColor" and set all the numbers in that line to zeros like (0.00, 0.00, 0.00) then the next line "Window.SetBackgroundBottomColor" and do the same. save and exit. one the next boot the screen will remain black with the Ubuntu logo and orange dots (not sure yet how to change dot colour but It's not so bad on a black background.

Next is the GDM... I found [this youtube video]("http://www.youtube.com/watch?v=4ZY-DKkfFrg")  that explains it well.
It goes like this:
At login press control+alt+F1, log in, then type “export DISPLAY:0.0” enter then “sudo -u gdm gnome-control-center” enter then  control+alt+F7.  Edit as  desired then control+alt+F8 

I decided to change the background to match my regular one which is the space collection, this way it gives a seamless look. Also I changed the theme to match mine which is a mix of clearlooks and glossy-P.

I am all about choices, Ubuntu is great but it should not have to be so hard to change the look if you want (It use to be much easier before 9.04).

---

### Post by andymorton on 2010-10-13
A lot of plymouth themes have install instructions in the 'read me' file. It's just a case of copying and pasting a few lines in to the terminal. 

andy

---

### Post by peakpc on 2010-10-14
Have been looking at a few on "Gnome-look" but haven't had time to try any yet. thanks for the info.

---

### Post by Half-Left on 2010-10-14
Do it this way:

```
sudo cp /usr/share/applications/gnome- appearance-properties.desktop /usr/share/gdm/autostart/Login Window
```

Log out. Change your settings&#65279; you want to use.

Login

```
sudo unlink /usr/share/gdm/autostart/Login Window/gnome-appearance-proper ties.desktop
```

---

### Post by Megaptera on 2010-10-14
Interesting new option to manage Plymouth at this thread:

[http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812)

---

