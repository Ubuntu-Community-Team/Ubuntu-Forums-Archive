---
title: "Desktop background questions..."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Rinzwind on 2006-06-11
If I use my mouse scroll on the volume control I can go up and down in volume.
If I use my mouse scroll in firefox I can go up and down a webpage.

So this got me thinking....

- Can I use the scroll on an empty desktop to cycle through backgrounds.
Let's say I have a ~./background/ with 100 pictures in it. I want to be able to switch my desktop at will by ticking 1 time on the mouse wheel. 
But only if I am scrolling on the desktop :) (gnome)

- Is it possible to have a dynamic webpage as a background? (gnome and kde)

---

### Post by %hMa@?b&lt;C on 2006-06-11
you can have four by default, scroll the mouse at the workspaces by the trash bin to change to a fresh desktop
another way to change is ctrl+alt+either left or right arrow

---

### Post by PriceChild on 2006-06-11
[quote=jeffc313]you can have four by default, scroll the mouse at the workspaces by the trash bin to change to a fresh desktop
another way to change is ctrl+alt+either left or right arrow[/quote]

No he's asking about changing the desktop wallpaper, not the workspace.

No ideas personally sorry :(

---

### Post by maddbaron on 2006-06-11
i was wondering the same thing. is there a way to have gnome automatically switch backgrounds like every 2days or however long u want it to take? that would be cool indeed.

---

### Post by nalmeth on 2006-06-11
I happen to really like the idea. hmmm You should try to submit it as a feature request for KDE 4.0, I think they must still be taking them. 

there is a tool for gnome to do slideshow wallpapers, can't recall what its called though. KDE has it by default

---

### Post by Jenda on 2006-06-18
Well, I can offer you a script that chooses random wallpapers upon running (for Gnome). You need to change the path inside. Then you can create a panel launcher that runs the script. it's not what you wanted, but almost :)
```
#!/bin/sh

#Name: ranwp.sh
#Function: Wallpaper randomiser
#Adapted for Ubuntu Warty from suggestions 
#found on http://gnome-hacks.jodrell.net/
#License: Public Domain

#Instructions: Place this script in a /bin directory
#and do a chmod +x <filename> on it.
#Then put it in a crontab or with your startup programs.
#Or both. Ubuntu Warty doesn't have a crontab editor, 
#but you can install gcrontab via synaptic.

cd /CHANGE/ME/PLEASE
#change this location if you keep your backgrounds elsewhere.
#Just one location allowed, sorry

IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
#You may want to get rid of the tiger head in 
#/usr/share/backgrounds/scalable, in fact, blow
#that directory away!

N=`echo $IMGS | wc -w`
#Find out how many pictures we got

((N=RANDOM%N))
#Take a random number between 1 and N

BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
#We have to cut twice to get rid of an irritating " ." at the 
#end after the first cut

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/jenda/Pictures/Obrazky/Background/$BGNAME"
# end of gconftool command

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
#Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"
# end of gconftool command


#That's it, your background should have changed.

```

---

### Post by ComplexNumber on 2006-06-18
[quote=maddbaron]i was wondering the same thing. is there a way to have gnome automatically switch backgrounds like every 2days or however long u want it to take? that would be cool indeed.[/quote]
there are quite a few applications that can do this. wallpapoz has cycling or randomising of wallpaper as well as the ability to have a different wallpaper on each virtual desktop. there is also WallpaperZapper and Wallpaper Tray.

---

