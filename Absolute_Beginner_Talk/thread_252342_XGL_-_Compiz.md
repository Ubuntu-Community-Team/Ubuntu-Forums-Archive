---
title: "XGL - Compiz"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-09-06
I got XGL up and running and it looks great works perfectly.

But I can't find where to access the controls.

Need both the theme manager and the button/key config.


P.S. If you want to install XGL, have gnome and an ATI card use this guide, its super easy, very n00b friendly:

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Thanks

---

### Post by zekopeko on 2006-09-06
if you mean the setup for all those plugin options install: cms

for themes install: cgwd and cgwd-extras 

and don't forget to edit your compiz startup script!

mine is in /usr/bin/startcompiz and it looks like this

```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &   
compiz --replace dbus csm &
cgwd --replace &
```

so do:

```
sudo gedit "place_where_you_put_your_script"
```

and replace gnome-window-decorator with cgwd

logout and login and that is that

---

### Post by redDEADresolve on 2006-09-06
I needed to download those files, THANKS!

---

### Post by redDEADresolve on 2006-09-06
I still need to figure out how to config XGL key mapping/controls.

Basically I want to get rid of the expose feature when placing the mouse in the right upper corner and lower left corner.

Thanks

---

