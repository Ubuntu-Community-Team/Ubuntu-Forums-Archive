---
title: "Internet speed with Ubuntu"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by natman on 2006-02-18
Hi, I work in collage and have broadband (T3 lan ) at home ( 2mbps), both of my computers have dual boot with windows xp.
With both i have noticed a significant slowing down of internet speed when i am just surfing ( downloads from ubuntu work fine ).
I use firefox/konqourer, is there any reason for this?, anyway to fix it?
thanks.

---

### Post by natman on 2006-02-18
Hi, thanks for all the views, but i eventually was able to sort this out using an old post which amounts to
> 1: sudo gedit /etc/modprobe.d/aliases
2: find the line - alias net-pf-10 ipv6
3: Edit this to alias net-pf-10 off
4:save and reboot
5: IF that does nothing try line 3) with .... off ipv6
6:It should now surf alot faster

---

