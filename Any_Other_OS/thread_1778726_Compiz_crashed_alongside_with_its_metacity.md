---
title: "Compiz crashed alongside with its metacity"
date: 2011-06-09
forum: Any Other OS
---

### Post by ak4allz on 2011-06-09
Please refer to this picture (snapshot of pidgin)
[IMG]http://i.imgur.com/MVW7V.png[/IMG]

As you can see, the metacity that wrap the Windows lost. And now, i can't use run dialogue (Alt-F2) & all windows border didn't appear... 

Now, for the temporary i open up the Compiz Fusion Icon, change the setting to "Metacity" instead of "compiz"

[IMG]http://i.imgur.com/O3On2.png[/IMG]

All of the nice 3D interface that powered up by the Compiz cannot be used anymore.

I'm using the Samsung Netbook NP148 with Intel Atom and Linux Mint 11.. I hope I can find the solution ASAP.. thanks

---

### Post by Perfect Storm on 2011-06-09
Moved to Other OS/Distro Talk.

---

### Post by osarusan on 2011-11-03
It's old, but since it's never been answered I thought I would post it here.

This crash happens when you press the menu icon on any window (the top left corner of the window).

This is a problem with the Window Decoration plugin in Compiz Config Settings Manager. You have to edit the line that says "Command" to say "/usr/bin/compiz-decorator" instead of whatever it normally says there. Then it should work.

---

