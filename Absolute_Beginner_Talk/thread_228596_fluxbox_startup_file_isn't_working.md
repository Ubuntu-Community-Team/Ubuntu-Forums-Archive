---
title: "fluxbox startup file isn't working"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Milis on 2006-08-03
hi

the fluxbox startup file at /home/user/.fluxbox/startup, isn't working for me. Everything I alter in that file, like background or startup apps, isn't executed when i restart

should i change an other file?

---

### Post by taurus on 2006-08-03
Can you paste your ~/.fluxbox/startup here?

```

more ~/.fluxbox/startup

```

---

### Post by Milis on 2006-08-03
```
b# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
bsetbg -f /home/user/foto\'s/1.jpg

# This sets a black background

#usr/bin/fbsetroot -solid black

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
# xset +fp /home/user/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
#wmsmixer -w &
#idesk &
wmMoonClock &

#  And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

```

Well i've got the moonclock to work

but the bsetbg isn't doing the trick for me. This is rather strange because when i type the line in a terminal, the background changes

---

