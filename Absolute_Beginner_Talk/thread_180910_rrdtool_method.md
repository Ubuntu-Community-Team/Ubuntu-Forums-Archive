---
title: "rrdtool method?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-05-23
Ive been searchin the web lookin for a  link where it uses rrdtool to graph the temperture readings in lm_sensors . Has anyone a clue where it is or even how to do it?

Thanks meniscus

---

### Post by lawina on 2006-10-04
My reply might be too late. It can be downloaded through synaptic.

---

### Post by ndegwajim on 2007-10-26
Someone installed NMIS on a linux box that i have. I'm trying to add more *.rrd files into the box but it doesn't seem to acknowledge the rrdtool command, even though a directory exists. :(

 How do i activate this command. I need to add more devices for monitoring purposes ?

 root@kclinux:/# ls  /usr/local/rrdtool/bin
                               [COLOR="Black"] rrdcgi  rrdtool  rrdupdate[/COLOR]


root@kclinux:/# rrdtool create test.rrd
[COLOR="Black"]bash: rrdtool: command not found[/COLOR]


Cheers

---

