---
title: "Google Earth through Proxy"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Gone fishing on 2007-09-26
I can't get Google Earth to run through a proxy without  connection failures unless I use a terminal and run

export http_proxy="192.168.1.1:8024" ; googleearth

If I add export http_proxy="192.168.1.1:8024" to my .bashrc file I can run 

googleearth from a terminal but still not from a short cut or the gnome menu any ideas

---

### Post by kyphi on 2007-09-26
I installed Google Earth via Automatix (not the flavour of the month at the moment) and have an icon in my Applications -> Internet menu.  It works perfectly.

To create a launcher right click on the top panel and then 'Add to panel'.  Select 'Create custom launcher' and tick 'run in terminal'.

You have to specify your path, of course.  ....and give the launcher an icon.

---

### Post by Gone fishing on 2007-09-26
Thanks but it starts OK the problem is I connect through a proxy and I cant find how to get googleearth to connect through the proxy other than running 

export http_proxy="192.168.1.1:8024" ; googleearth

in a terminal then it works fine but its not very slick having to start in a terminal

I suppose gnome has its own bashrc where is it?

---

### Post by kyphi on 2007-09-26
Stellarium is a stargazer programme that has to be started in the terminal.  I got fed up with that and created a custom launcher as described.

Put 'export http_proxy="192.168.1.1:8024" ; googleearth' as your path statement and tick the terminal.

---

