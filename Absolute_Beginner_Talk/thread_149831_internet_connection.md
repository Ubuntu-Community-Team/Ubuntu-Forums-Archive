---
title: "internet connection"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by steelgrave on 2006-03-24
used [COLOR="RoyalBlue"]pppoeconf[/COLOR] to install and all is workin but the connection terminates every 5-10 mins so i have to dial again/ ([COLOR="Blue"]pon dsl-provider[/COLOR])
and what is MRU, MTU

---

### Post by Pragmatist on 2006-03-24
MRU = Maximum Receive Unit
MTU = Maximu Transmit Unit

You can play with those in /etc/ppp/options  I'm not sure whether or not this is your problem, but since you mentioned MRU/MTU I though you'd be interested.

---

