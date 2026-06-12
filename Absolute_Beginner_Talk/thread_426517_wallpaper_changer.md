---
title: "wallpaper changer?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-04-28
is there a simple wallpaper changer? i found one on linux.org but the download was broken. i just want to be able to specify a folder from which to get images, and the time between switches. also preferable but not required to have some effects like fading into black, then into the next image.

---

### Post by kittyhawk63 on 2007-04-28
> **supersonicdarky said:**
> is there a simple wallpaper changer? i found one on linux.org but the download was broken. i just want to be able to specify a folder from which to get images, and the time between switches. also preferable but not required to have some effects like fading into black, then into the next image.

There is a default one with Ubuntu. System->Preferences->Theme. Check forum and Google search for others.
kh

---

### Post by annda on 2007-04-28
wallpaper-tray is in the repositories

"wallpaper changing utility for GNOME
This utility sits in your GNOME Panel Notification Area. It sets a random
wallpaper from a list of directories either at login, on a regular basis
or on demand."

synaptic is your friend :-)

---

### Post by kittyhawk63 on 2007-04-28
> **annda said:**
> wallpaper-tray is in the repositories
"wallpaper changing utility for GNOME
This utility sits in your GNOME Panel Notification Area. It sets a random
wallpaper from a list of directories either at login, on a regular basis
or on demand."
synaptic is your friend :-)

I apologize for the jump in:
Annda, have you used this and how many wallpapers does it show? Can you see the wallpapers for making the selection.
kh

---

### Post by supersonicdarky on 2007-04-28
thnx =D

i almost never use synamptics, only terminal, so i didnt know it existed

---

### Post by jordanmthomas on 2007-04-28
Well, I have a question along the same lines:
How would I go about changing the wallpaper in Gnome via a command line?  I'd imagine it would have something to do with gconf maybe?

Once exams are over I was going to learn python and I figured writing a wallpaper changer would be a good first project for me...I just don't know how to change the wallpaper.

---

### Post by yabbadabbadont on 2007-04-28
> **jordanmthomas said:**
> Well, I have a question along the same lines:
How would I go about changing the wallpaper in Gnome via a command line?  I'd imagine it would have something to do with gconf maybe?

Once exams are over I was going to learn python and I figured writing a wallpaper changer would be a good first project for me...I just don't know how to change the wallpaper.
```

gconftool -t string -s "/desktop/gnome/background/picture_options" "none"
gconftool -t string -s "/desktop/gnome/background/picture_filename" "/path/to/new/wallpaper/imagefile"
gconftool -t string -s "/desktop/gnome/background/picture_options" "zoom"

```
Change the "zoom" to whichever option your prefer.

---

### Post by annda on 2007-04-28
hi jordan,

you will probably need gconftool-2.

as for python wallpaper ideas, take a look here:
[http://chakravyuh.blogspot.com/2005/10/gnome-wallpaper-switcher.html](http://chakravyuh.blogspot.com/2005/10/gnome-wallpaper-switcher.html)

and here (in german, but code is in python):
[http://www.python-forum.de/viewtopic.php?=&p=54135](http://www.python-forum.de/viewtopic.php?=&p=54135)

and a script mentioned here:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_set_up_.28automatic.29_background.2Fwallpaper-changer_application_for_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_set_up_.28automatic.29_background.2Fwallpaper-changer_application_for_GNOME)

and this collection:
[http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/](http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/)

ii don't use it, but wallpaper-tray, which i suggested, seems to be problematic on ubuntu. and the latest sources are from 2005, so they can't be compiled without serious downgrading. i got it to work - not the applet though - but time change doesn't work. bummer.

but i'd enjoy a nice script, so go ahead and post when you are ready!

---

### Post by yabbadabbadont on 2007-04-28
> **annda said:**
> hi jordan,

you will probably need gconftool-2.

as for python wallpaper ideas, take a look here:
[http://chakravyuh.blogspot.com/2005/10/gnome-wallpaper-switcher.html](http://chakravyuh.blogspot.com/2005/10/gnome-wallpaper-switcher.html)

and here (in german, but code is in python):
[http://www.python-forum.de/viewtopic.php?=&p=54135](http://www.python-forum.de/viewtopic.php?=&p=54135)

and a script mentioned here:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_set_up_.28automatic.29_background.2Fwallpaper-changer_application_for_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_set_up_.28automatic.29_background.2Fwallpaper-changer_application_for_GNOME)

and this collection:
[http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/](http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/)

ii don't use it, but wallpaper-tray, which i suggested, seems to be problematic on ubuntu. and the latest sources are from 2005, so they can't be compiled without serious downgrading. i got it to work - not the applet though - but time change doesn't work. bummer.

but i'd enjoy a nice script, so go ahead and post when you are ready!
At one time or another, I tried most of those.  Most seemed to work fine, but none of them did a very good job of handling a **really** large wallpaper collection.  (over 50,000 images)  I ended up using a combination of bash shell scripts, cron jobs, and a simple random number generating program that I wrote.  (The bash $RANDOM built-in is limited to 32K)

---

### Post by jordanmthomas on 2007-04-28
Thanks a lot.  I figured it would be something with gconftool, I was just too lazy to fire up gconf-editor to find the wallpaper string.  

I'm sure this will help me a lot.

---

### Post by Drakkor on 2007-04-29
I installed wallpaper-tray, but it wasn't in any appiications I saw, the only way to get it to run is via the terminal, \which must be left on in the taskbar in order for it  to run, can I somehow make it auto start on boot, or launch it without the terminal ?  Thanks :)

---

### Post by jordanmthomas on 2007-04-29
system --> preferences --> sessions
go to the startup tab
add a new command for wallpaper-tray

Now, when you log in, it will be launched and stay running until you quit or log out.

---

### Post by Drakkor on 2007-04-29
Kewl !! :)  Thanks, jordanmthomas  worked like a charm !! :)

---

