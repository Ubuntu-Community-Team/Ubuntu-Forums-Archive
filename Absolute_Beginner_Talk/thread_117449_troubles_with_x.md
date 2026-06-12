---
title: "troubles with x"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by solstis on 2006-01-14
hey guys
it's around 6 a.m. here, and it's been one horrible night for me and my friend
he tried to guide me through a problem.
i do everything by the book on the x-configuration and when it get's to the question about the color bits. when i choose something a msg pops under the config 
xserver-xorg postinst warning : overwriting possibly-customized conf file; backup in etc/X11/xorg.200601121720

we also noticed the error in the framebuffer device so i said 'no' on the question tried to erase the file and do the thing again..
same thing
also it says that the xserver is disabled because the config was not setup right

i'll fill you in with more details when i get some sleep..

any ideas ?

---

### Post by fourchannel on 2006-01-14
what it's saying is that it's about to overwrite your xorg.conf file and set it up with the new info. Tell it YES, cause it will backup your old file should anything go wrong. But you were on the right track, just tell it yes this time and see what happens.

---

### Post by solstis on 2006-01-15
it's not like that actually
it kind of informs me of that cause after the lines i quoted there's the well known   user@host, in my case
root@snail*# (not sure about the last symbols but i think you get the idea ;) 
no y/n option

---

