---
title: "default gateway in a bash variable?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by decker on 2006-07-31
I'm pretty familiar with sed but not awk, whats the best way to get the gateway IP address in a variable that I can use i a bash script?

so far i've got

GW=`route -n |tail -n1|cut -d' ' -f10`

is there a better way to do this?

---

