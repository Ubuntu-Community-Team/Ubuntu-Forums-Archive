---
title: "Problems with window positioning"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by PhilippHD on 2006-07-08
Hi @ all,
here's the problem:
Whenever I open a new window (ie Terminal or Firefox) it pops up and places itself at the top of the screen with the titlebar behind the startbar. I have to rightclick on its entry in the taskbar and reposition it. How can I adjust it, so it doesn't pop up at the top of the screen but a little lower ?

thx

---

### Post by zerwas on 2006-07-08
Hi,

A question: Do you use the 3D windowmanager compiz with XGL/AIGLX?

Greetings,
zerwas

---

### Post by PhilippHD on 2006-07-08
Yes, i use Compiz/XGL.

---

### Post by someusernoob on 2006-07-08
[http://xgl.compiz.info/](http://xgl.compiz.info/)

Did you add those to your sources.list?

Never had a problem with Compiz or XGL while using this repo for Compiz updates, although they update almost every day.

---

### Post by PhilippHD on 2006-07-08
Yes, they are in the sources.list and I just updated them this morning.

---

### Post by someusernoob on 2006-07-08
Do you have gset-compiz installed?

```

sudo aptitude install gset-compiz

```

Check under the plugin section:
Move > both checkboxes. I have "constrain y" unchecked, and "snapoff max. windows" checked. Maybe you can give this a shot.

And it helps once in a while to reset the settings of Compiz. 

Log off, restart X (ctrl+alt+backspace) and do not let Compiz load when you log in.

Then open a terminal and type:
```

gconftool-2 --shutdown

gconftool-2 --recursive-unset /apps/compiz

```

Log off and restart X again. When you login in and start Compiz it is setted to the default settings. You can edit the settings using gset-compiz.

---

### Post by PhilippHD on 2006-07-08
@someusernoob:
maybe that could help, too

anyway, i found the reason:
yesterday i deactivated the place-plugin, after re-activation the windows are well placed again.

thx anyway

---

### Post by someusernoob on 2006-07-08
Glad to hear you solved it yourself. Altough i advise you to save the commands i gave on how to reset Compiz. If in the future you deactivate/change options, and you do not remember what you actually changed, you can just reset Compiz without searching the net for a few minutes finding those codes again. :P

---

### Post by thnogueira on 2006-07-14
> **PhilippHD said:**
> @someusernoob:
maybe that could help, too

anyway, i found the reason:
yesterday i deactivated the place-plugin, after re-activation the windows are well placed again.

thx anyway

In my case this solution didn't work. I got the solution from Compiz forum
[http://www.compiz.net/viewtopic.php?id=1778](http://www.compiz.net/viewtopic.php?id=1778):

```
Post starter prolly didn't and relied on gset-compiz to tweak setting.

gconf-editor: /apps/compiz/plugins/move/allscreens/options/

Toggle: constrain_y
```

This solution solved my problem :)

---

