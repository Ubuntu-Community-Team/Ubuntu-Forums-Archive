---
title: "how to get function keys on macbook to work with other window managers?"
date: 2017-05-09
forum: Apple Hardware Users
---

### Post by ncdirtbag on 2017-05-09
Ive got Ubuntu with MATE  installed  on my macbook and if Im using mate, the function keys work fine for adjusting the 
1. volume
2. screen brightness
3. keyboard brightness.
4. multimedia pause/play
5. etc.


If I run a  different window manager like backbox or icewm, I cannot get the function keys to work. 
Is there a way to get that functionality with a window manager like icewm?

-db

---

### Post by QIII on 2017-05-09
Moved to ***Apple Hardware Users*** for a better fit.

---

### Post by &amp;KyT$0P# on 2017-05-09
Are you using these window managers under MATE, replacing MATE's default window manager?  Or are you logging in to these window managers' sessions?

---

### Post by ncdirtbag on 2017-05-10
yeah, I was not using MATE at all. Just using straight up icewm or openbox.

-db

---

### Post by &amp;KyT$0P# on 2017-05-10
Well one answer might be to just replace MATE's window manager with your window manager of choice, and go with that.  For example, if you want to use Openbox that way, you just do this inside MATE -
```
openbox --replace
```
I do precisely that under Xfce and the keys still work as before.

If you specifically want to use the window managers' sessions.  Most likely the keys are handled by programs that MATE starts, but these other window managers do not.  For example, in Xfce the brightness keys are handled by the power manager, and the volume keys by the sound indicator.  See if you can find which MATE programs are handling the keys you need and see if you can get them to work in your window manager session of choice.

I don't know MATE, so I probably won't be much more help than that, sorry.

---

### Post by ncdirtbag on 2017-05-10
well thanks, i tried the "openbox --replace"
and that certainly did give me openbox, but it did not give me the "right-click" menu in openbox that I am familiar with. 
Is there a way to get that working in mate? thats the real reason I want to run openbox or icewm.. 

-db

---

### Post by &amp;KyT$0P# on 2017-05-10
Should be possible.  Try editing [FONT=Courier New]~/.config/openbox/rc.xml[/FONT] to add a keybinding for that menu.  For example, this...
```
    <keybind key="W-X">
      <action name="ShowMenu">
        <menu>root-menu</menu>
      </action>
    </keybind>
```
... should make it accessible with Command-X.  (Adjust accordingly if your [FONT=Courier New]rc.xml[/FONT] lists something different than [FONT=Courier New]root-menu[/FONT] for right mouse button under [FONT=Courier New]<context name="Root">[/FONT].  Or if you prefer a different key combination.)

To apply the change, just run in Terminal -
```
openbox --reconfigure
```

Refer to Openbox documentation, e.g. [this]("http://openbox.org/wiki/Help:Configuration"), for more info.

---

