---
title: "Real Player won't start!"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by shador on 2005-08-07
Does anyone know why my RealPlayer 10 won't start? I've tried starting it in the terminal with sudo ande i've tried to open it in "run" but the program won't start :'( 

A little help please :)

---

### Post by SFN on 2005-08-07
A couple of questions.

How did you install it? How are you starting it?

Ideally, you should have just done "sudo apt-get install realplayer" to install it. If you did that, try starting it from the command line by opening a terminal typing in "reaplay". Copy and paste any errors you get here.

---

### Post by TravisNewman on 2005-08-07
actually, when I apt-get install'd realplayer it didn't work either.

---

### Post by SFN on 2005-08-07
I had that problem when I first installed and ended up using tyhe Helix player. I read somewhere here that others were not having that problem so I tried "apt-get install reaplayer" again. Worked fine after that. I assumed that somebody had changed the package in between the first time I tried it and the second time.

---

### Post by npaladin2000 on 2005-08-07
Well, so far it isn't working for me.  Apt-get didn't work (it couldn't find the downloaded file), installing from bin (realplayer10) didn't work; it just won't start (run the script and the terminal just sorta sits there forever).  Same with alien-ing the RPM version.

---

### Post by shador on 2005-08-07
It's still not working. But it's ok now, i found the mediaplayer xine and that works perfectly for me :) It plays everything

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=shador]It's still not working. But it's ok now, i found the mediaplayer xine and that works perfectly for me :) It plays everything[/QUOTE]

Good. I like Gxine best- its the Gnome xine.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=poofyhairguy]Good. I like Gxine best- its the Gnome xine.[/QUOTE]

Realistically, what's the difference between Gxine and Totem-xine? ;)

---

### Post by jamesrw on 2005-08-19
i also cannot get realplayer to run.. how do i uninstall it??  i had downloaded the .bin file from the website.

---

### Post by jamesrw on 2005-08-21
i got it to start by unchecking [enable sound server startup] in system > preferences > sound. That prevented sounds in some other apps from playing, and  had to choose different sound outputs. It runs really choppy though, not sure why. I tried changing the cpu settings in the the app but no luck. Are there any alternatives to streaming real audio?

---

### Post by TristanMike on 2005-08-21
I remember seeing LOTS of people with Realplayer problems and have seen many threads about this subject. In a quick search I pulled these up. Apartently it's a problem with ESD confilct, but check these out, they may help....

[http://www.ubuntuforums.org/showthread.php?t=21462&highlight=Real+Player](http://www.ubuntuforums.org/showthread.php?t=21462&highlight=Real+Player)

[http://www.ubuntuforums.org/showthread.php?t=53166&highlight=Real+Player](http://www.ubuntuforums.org/showthread.php?t=53166&highlight=Real+Player)

[http://www.ubuntuforums.org/showthread.php?t=47162&highlight=Real+Player](http://www.ubuntuforums.org/showthread.php?t=47162&highlight=Real+Player)

The last one may be most helpful, sorry for the links but I'm not fluent enough to help anybody except with the search button.  I hope some of this enlightens....

---

