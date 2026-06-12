---
title: "simple Script - Need (a few) command(s)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-12-09
I need a couple of things:
[LIST=1]
[*]A command for showing what hour it is in 24 hour form, or the whole time, but just the hour would be best :D
[*]A command for changing the background... and it should take effect ASAP, like, within a few seconds :p[/LIST]This is for changing my background automatically - I made a few sweet 3D pics, and they're all of the same scene, but different times of day... and I think this would be way cool :p

---

### Post by nikoPSK on 2007-12-10
I don't know but intend to find out. Can I see the wallpapers and how did you make em? :KS

---

### Post by PointyWombat on 2007-12-10
The following will show you what hour it is.
```
date +%H
```


For more info on the date command:
```
man date
```

HTH,

---

### Post by GSF1200S on 2007-12-10
> **ryanVickers said:**
> I need a couple of things:
[LIST=1]
[*]A command for showing what hour it is in 24 hour form, or the whole time, but just the hour would be best :D
[*]A command for changing the background... and it should take effect ASAP, like, within a few seconds :p[/LIST]This is for changing my background automatically - I made a few sweet 3D pics, and they're all of the same scene, but different times of day... and I think this would be way cool :p

Haha, I could give you the wallpaper changing script for KDE, but unfortunately not for Gnome. You know, I need to return to my roots and get a Gnome desktop rolling again...

---

### Post by ryanVickers on 2007-12-10
I used Bryce 5 - I know it's not the open source way :p, but I do not intend to release the full things, and especially the source files, but I'll show them at 700x560 ;)

NEWS FLASH! - we've got the time command! ;) Thanks :)

And to GSF1200S - I know :p, KDE has that built in am I right? but not gnome yet... lol and even so, I need it to be at certain times and not just after a period of time ;)
I'm thinking is there some way to change the equivalent of C:\Documents and Settings\%user%\Local Settings\Application Data\Microsoft\Wallparer1.%file_extension% (in windows) and then refresh the desktop? (don't be mislead by my knowledge of this, I can script in BASH quite well ;))

---

### Post by jordanmthomas on 2007-12-10
To change a wallpaper you can use gconf-tool
```

FILENAME=/path/to/file
gconftool-2 --type string --set /desktop/gnome/background/picture_filename $FILENAME
```
(you don't have to use a variable for the filename but I did it for readability's sake.)
This should take place instantly.

---

### Post by PointyWombat on 2007-12-10
I found the below script at [this link ]("http://gnome-hacks.org/hacks.html?id=6") and tested it and it works.

```

#!/bin/bash
IMGS=`find /usr/share/backgrounds -name \*.jpg`
N=`echo $IMGS | wc -w`
((N=RANDOM%N))
gconftool-2 -t str -s /desktop/gnome/background/picture_filename "`echo $IMGS | cut -d ' ' -f $N`"

```

---

### Post by ryanVickers on 2007-12-10
ok, thanx everyone, I'll write this up when I get back to Linux... anyone wanna help with [that]("http://ubuntuforums.org/showthread.php?t=636545")? :p

---

### Post by ryanVickers on 2008-01-02
Ok, linux is booting fine now - no real trouble, just booted recovery mode, installed the updates, and now my script is almost done...

---

