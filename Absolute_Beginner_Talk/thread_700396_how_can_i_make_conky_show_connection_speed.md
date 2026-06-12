---
title: "how can i make conky show connection speed"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-18
does anyone know how to make conky show the active internet connection speed?

---

### Post by sabatron on 2008-02-18
Is this what you're looking for?

[http://ubuntuforums.org/showthread.php?t=644463]("http://ubuntuforums.org/showthread.php?t=644463")

---

### Post by brokenhachi on 2008-02-18
not sure.... im not quite sure what he is talking about and there is no picture of his display.........


what i want is just like a number that shows my active connection speed.. for instance, "100mb/s" or whatever and maybe a graph..?

---

### Post by Kerry_W on 2008-02-18
Try this:


${color lightgrey}Down:${color #8844ee} ${downspeed eth0} KB/s${color lightgrey} ${offset 78}Up:${color #22ccff} ${upspeed eth0} KB/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${alignr}${upspeedgraph eth0 32,150 0000ff ff0000}
${color0}total-in: ${color}${totaldown eth0}${offset 78}${color0}total-out: ${color}${totalup eth0}

---

