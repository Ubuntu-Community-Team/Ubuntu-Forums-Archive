---
title: "Disble wavy tooltips or menus in Beryl"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-11-11
Is this possible? They are really bugging me.

Also, can anyone tell me how to hide the gem icon next to my clock? Thanks in advance.

---

### Post by strabes on 2006-11-11
Right click on the red gem icon, and then go to beryl settings manager. You can change that stuff in the Animations plugin.


The gem icon is for beryl-manager. To 'disable' it you could do two things: You could turn off your notification area which would depend on whether you use other things in the notification area like network-manager-gnome, etc. 
Or, you could disable the gem icon only temporarily just run 'killall beryl-manager' 
To disable it from starting up with gnome, remove it from the Startup Programs tab of gnome-session-properties. It doesn't have to be running in order to get the 3d effects, just to change settings.

Does this help you?

---

### Post by jordanmthomas on 2006-11-11
I'm pretty sure in beryl-settings, you do need to disable Tooltips in the Animations plugin.  Also, the wobbly plugin might have some stuff you can disable.

To get rid of the icon, but still use beryl, you can run beryl-start instead of beryl-manager.  Then, you don't have to worry about killing it every time and you'll get to keep your notification area.

---

### Post by Chayak on 2006-11-11
Ok, go to beryl-manager > Beryl settings manager > Animations > (the default) is create effect 2 and close effect 2 > change it to what you want, I prefer zoom or fade for tooltips myself.

---

### Post by Charco on 2006-11-11
You guys are so awesome! I have one last thing though, when I run gnome-session-properties, Beryl isnt listed...

---

