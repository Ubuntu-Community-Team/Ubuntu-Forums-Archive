---
title: "Possible to change the title bar of rox ? (a bit like Eterm -n title2)"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-01
Hi,

Is it possible to change the title bar of rox ? (a bit like Eterm -n title2)
not to display the folder location, but to display in the title bar a fixed name (title) like for instance ROX-filer-window-01
(rox-filer)

Thank you very much,

Patrick
(fvwm underneath ... for a window autohidding...)

In fvwm I can do this: > # Change the tile of a window
Key T WSFT 3 PipeRead 'echo Module FvwmForm FormWindowTitle WINDOWID=$[w.id] OLDTITLE="\\\"$[w.name]\\\"" POSX=$$$$[ ($[w.width] - 310) / 2 + $[w.x] ] POSY=$$$$[ $[w.y] + 4]'

But, I would like to start the rox from xterm with mentioning its new title;...
like : rox --title hello 
for instnace 

thx

---

