---
title: "Plugin's."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by newbreed9000 on 2006-08-23
I cant seem to get Myspace or Google video's to run. What do I need to do? I am newb. I used Automatix and downloaded all that I beleived to be appropriate. Like the Firefox 1.5 plug in's I beleived would be enough. Help?

Also I cannot seem to fund out how to change my resolution. I get to the option but the size i want just isnt available. I would like 1280x1024 with 75refresh. <3

---

### Post by baldy1324 on 2006-08-23
make sure you download the flash player plugin in automatix b/c i think this is what google and myspace use. and for resolution-type ```
gksudo "gedit /etc/X11/xorg.conf"
``` the go down to part where it says Screen and the Subsection Display and on all of the lines with the resolution (1024x768....)insert 1280x1024 on all every single line that has the other resolutions. as for refresh rate-i have no idea.:cool:

---

