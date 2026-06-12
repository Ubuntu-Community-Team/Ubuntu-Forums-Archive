---
title: "fluxbox"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-12-14
i found a howto for fluxbox

[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

I tried this option

b) Use you're start up file. Type nano ~/.fluxbox/startup (if it does not exist, create it) and put this in there
Code:

exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

i press ctrl = o to save the and it shows this
[B]
File Name to Write:[/B]

what do i have to put hare????

pls help i want to try fluxbox

---

### Post by kerry_s on 2006-12-14
Well it would be "startup" but if you use ctrl + X and Y and enter you won't have that problem. You can also just use a regular editor. Instead of compiling you should have just grabbed it from the repo with synaptic or apt-get then everything would have been in the right place and you would just uncomment it.

# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/user/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/user/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/user/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

/home/user/.startup &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"

---

### Post by fasoulas on 2006-12-14
> **kerry_s said:**
> Well it would be "startup" but if you use ctrl + X and Y and enter you won't have that problem. You can also just use a regular editor. Instead of compiling you should have just grabbed it from the repo with synaptic or apt-get then everything would have been in the right place and you would just uncomment it.

# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/user/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/user/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/user/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

/home/user/.startup &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"


What to do with all that u posted???

I tryied this way because in synaptic it is an older version of fluxbox

---

### Post by kerry_s on 2006-12-14
Newer is not always a good thing, the one in the repo is well tested & stable.
You don't need to do anything with it i was just posting what mine looks like in case your making yours from scratch.

---

### Post by fasoulas on 2006-12-15
> **kerry_s said:**
> Newer is not always a good thing, the one in the repo is well tested & stable.
You don't need to do anything with it i was just posting what mine looks like in case your making yours from scratch.

ok thnx if u were tring to help i finally made it work but every time i log in with fluxbox i see the default theme the blue one the **meta** and when i change it and log off or shut down the default theme cames back

Also how can i put a wallpaper??

---

