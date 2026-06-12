---
title: "Warcraft Tft port opening"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by MaZZly on 2006-03-27
hi!
i started using ubuntu 4 days ago on my new server :)
and i have the internet shared trough the server (internet -> server -> my winxp machine)
but when i try to host custom games in warcraft3(Dota) i cant get anyone to join.

So could any1 here want to tell me how to open port: 6112-6119 Tcp in/out on my ubuntu machine

*edit* im playing from my xp machine

---

### Post by MaZZly on 2006-03-27
anyone knows how to open ports in ubuntu?

---

### Post by Coocks on 2006-03-29
If you are using windows xp sp2, the firewall might be blocking it aswell. I had the same problem a while back and the only solution was to disable the sp2 firewall.

---

### Post by MaZZly on 2006-03-30
im using sp1 (my computer gets some problems with sp2)
and i can host games on bnet if i put the dsl cable right to my computer (not via server)

i tried installing firestarter and allowed port 6112-6119 and i also allowed things coming from ip 192.168.0.2 (my xp machine)
and i put on the "permissive by default, blacklist traffic"
And i also pressed "apply policy"


*edit* finally got it working, here is what i did:
forwarded port 6112-6119 to ip 192.168.0.2(xp) on port 6112-6119

thnx for the help!

---

