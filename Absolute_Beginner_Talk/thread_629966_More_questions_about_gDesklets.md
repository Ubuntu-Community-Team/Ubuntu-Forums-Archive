---
title: "More questions about gDesklets"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2007-12-02
The first time i open gDesklets i got this message:

Please note that due to limitations of older X servers, you might see blocks around desklets in Float mode. This cannot be solved in a satisfying way except for switching the X server to real translucency (Xorg 6.8 and above).

Does anyone know how to switch the x server and what side effects could that have? Is there anyway to get rid of the ugly shadow around the Launchbar?

---

### Post by G. Cotgreave on 2007-12-03
Anyone?...

---

### Post by G. Cotgreave on 2007-12-03
Ok i solved the problem with the shadow. Log in as root and open /usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display in the begining of the file you will find this

```
<!-- the panel with borders -->

  <frame watch="x=iconbar:panel-x, y=iconbar:panel-y,
                width=iconbar:panel-width, height=iconbar:panel-height"
         border-width="4, 4, 4, 4"
         border-uris="gfx/bg-w.png, gfx/bg-n.png, gfx/bg-e.png, gfx/bg-s.png,
                      gfx/bg-nw.png, gfx/bg-ne.png,
                      gfx/bg-se.png, gfx/bg-sw.png">
    <group id="panel" bg-color="#3a416ba0" width="100%" height="100%"
           watch="bg-uri=iconbar:background"/>
  </frame>
```

in the line ''border-width="4, 4, 4, 4" change all the numbers from 4 to 0 and restart the desklet.

I am sure there is a way to do it without loging as root but straight from the terminal with sudo but i#m still new and i don't know how.

As for that x-server thing i still don't have a clue!!!

---

### Post by jken146 on 2007-12-03
Practically any command can be run as root with sudo.  Just put sudo before the command.  If you want to do things in a GUI manner, you can use gksudo.  For example, to start the file browser Nautilus with root privileges, hit Alt+F2 and type ```
gksudo nautilus
``` (or type it in a terminal).  This will save you having to keep logging in as root.

---

### Post by G. Cotgreave on 2007-12-03
Thnx!!! and i was wondering how to open nautilus with root privileges for something else i wanted to do!!!

---

