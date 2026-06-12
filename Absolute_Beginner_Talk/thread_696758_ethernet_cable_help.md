---
title: "ethernet cable help"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Radical62 on 2008-02-14
Well ive used XP for years and am very experienced with it, and the other day i installed ubuntu and run it with dual-boot.  the problem is when my ethernet cable is plugged in, ubuntu still doesn't pick up the connection.

NOTE: i was tweaking xorg.conf to allow my external monitor to work and i messed up the first time so i had to reinstall.  before this reinstall the internet worked fine.

---

### Post by Cypher on 2008-02-14
Show us the output of
```

ifconfig -a
cat /etc/network/interfaces
lspci | grep Ethernet

```

---

### Post by jonnywombat on 2008-02-14
I have had a similar issue in the past where on a dual boot machine ubuntu would not pick uo the ethernet connection.

This for me would only happen when I had been using windows and switched to ubuntu via a shutdown or restart. 

The only way I found of sorting this was to completly power down the machine (shutdown and then pull out the power chord for a few seconds) then it would work just fine until next time I booted into windows, when I would have to repeat the process.

Jonny

---

