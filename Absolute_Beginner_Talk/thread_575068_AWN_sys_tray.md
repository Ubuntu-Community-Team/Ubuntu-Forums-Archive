---
title: "AWN sys tray?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-13
System tray wont show up all it shoes is a white bar.

Also the bar doesn't extend as more programs gets opened.

[IMG]http://i20.tinypic.com/2zfvbev.png[/IMG]

---

### Post by llamakc on 2007-10-13
OH! SO that's what that is. Hah. I get the same issue here.

---

### Post by InsertNameHere on 2007-10-13
Also as more items get on the try the tray itself doesn't extend.

And the seperators don't move at all.

---

### Post by mpgarate on 2007-10-13
happens to me too! somtimes just leaving it alone for awhile works...

---

### Post by InsertNameHere on 2007-10-13
It doesn't happen over time to me...

I start it, its like that...

---

### Post by defrex on 2007-10-13
... Though I'm sure it must work for some people, because they included it in 0.2, I've yet to meat someone with a proper systray in awn. I love awn, but it's just not ready for me to be ready of gnome panels all together.

---

### Post by InsertNameHere on 2007-10-13
So is it just going to be like that and nothing can fix it?

---

### Post by defrex on 2007-10-13
Ya, it's a bug. You could always try and dig into the code yourself. Make sure you pass on the patch so I can use it too. :)

---

### Post by JBAlaska on 2007-10-13
On my system this was caused by a applet that awn was trying to start, but I really don't remember which one.

---

### Post by altonbr on 2007-10-14
I have the same problem.

AWN isn't stable enough for production so I removed it and when back to the Gnome Panels. It still has a lot of functionality issues to which really pissed me off.

I'd advise living with it or removing it for now.

---

### Post by jordanmthomas on 2007-10-14
If you still have a notification area in your gnome panels the awn system tray won't load.  Could this be any of y'alls issue?

(system tray works fine here)

---

### Post by zeusalmighty on 2008-01-20
+1 for the previous post! My awn and applets wasn't working correctly, until I removed systray from the gnome-panels. Better yet, kill all gnome panels permanently if you don't need them anymore!

[Check here]("http://ubuntuforums.org/showthread.php?t=652367&highlight=awn+applets")

---

### Post by wford002 on 2008-02-06
Thanks, that fixed it.

---

### Post by Nythain on 2008-02-10
ok, so i have a few problems...
First... i cant get teh notifier (system tray) to work for squat... same problem as above and killing other daemons doesnt work
Secon... how can i keep gnome panel from loading... i tried killing it, it just came right back...

i can live without an awn system tray, ill just throw in a pypanel or similar panel or dock for the system try... but i want the gnome panel GONE!!!

---

### Post by miq on 2008-02-11
As far as i know, there is no way to remove the last gnome panel, but you can hide it.
Mine is put on the left, transparent, expanded, with no arrows, no buttons. 
In gconf-editor  /apps/panel/toplevel/panel_0(or your panel id)/ you put
auto_hide = true, auto_hide_size = -100, uhide_dely =0, unhide_delay=60000.
This way, you'll never seen it anymore (sometimes a line on the left when you log...)

---

### Post by jordanmthomas on 2008-02-11
You can get rid of gnome-panel in your system -- preferences -- sessions.
You just have to take it off the mode that restarts it when it dies and then kill it.

edit:  or, if you don't want gnome-panel, consider just using your own script to start x with.
Mine:
```
#!/bin/sh

#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
xmodmap ~/.Xmodmap
xbindkeys
[COLOR="Silver"]#gnome-volume-manager &
#awesome-monitor &
#xcompmgr -cC &[/COLOR]

feh --bg-scale "/home/jordan/wallpaper/radm.jpg"
conky &

[COLOR="Silver"]#exec dbus-launch --exit-with-session --auto-syntax startkde
#exec gnome-session
#exec awesome[/COLOR]
exec compizstart #a script I wrote to get compiz started properly

```

You can install a custom session in gdm by copying one of the files in /etc/X11/sessions and modifying it to run your own startup script (or you can just use startx and not use gdm)

---

### Post by edg on 2008-02-12
> **InsertNameHere said:**
> System tray wont show up all it shoes is a white bar.

Also the bar doesn't extend as more programs gets opened.

[IMG]http://i20.tinypic.com/2zfvbev.png[/IMG]

Could you tell me what clock you are using? I like the transparent type frame around it. Thanks.

---

