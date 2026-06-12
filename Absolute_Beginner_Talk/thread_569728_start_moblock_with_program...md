---
title: "start moblock with program.."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by gav616 on 2007-10-07
i need a script to start moblock when i execute BitTornado, then when i end 'btdownloadgui' (BitTornado)
moblock exits too.

The reason is i prefer only to use ip blocking when doing p2p.

I know i could just start moblock myself with a simple cmd, but i want to see how it would be done in a script.

couple of cmds to use in the *sh,
btdownloadgui (BitTornado)
moblock-control start (starts MoBlock)
moblock-control stop (stops MoBlock)

thank you.

---

### Post by gav616 on 2007-10-08
bump

---

### Post by wilberfan on 2007-10-10
I'd be interested in this, too!   :)

---

### Post by gav616 on 2007-10-11
either its unanswerable, or people are sneaky and wont release this infomation!! :(

BUMP

---

### Post by wilberfan on 2007-10-11
It's probably ridiculously easy--and no one can believe we can't figure it out!

---

### Post by gav616 on 2007-10-13
well ive done a temp solution,
using every blocklist i.e.....
```
bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz
bluetack.co.uk/config/bogon.gz
bluetack.co.uk/config/dshield.gz
bluetack.co.uk/config/edu.gz
bluetack.co.uk/config/fornonlancomputers.gz
bluetack.co.uk/config/gnutella.gz
bluetack.co.uk/config/hijacked.gz
bluetack.co.uk/config/iana-multicast.gz
bluetack.co.uk/config/iana-private.gz
bluetack.co.uk/config/iana-reserved.gz
bluetack.co.uk/config/level1.gz
bluetack.co.uk/config/level2.gz
bluetack.co.uk/config/level3.gz
bluetack.co.uk/config/Microsoft.gz
bluetack.co.uk/config/rangetest.gz
bluetack.co.uk/config/spider.gz
bluetack.co.uk/config/spyware.gz
bluetack.co.uk/config/templist.gz
bluetack.co.uk/config/trojan.gz
```

....then slowly unblocking ips that block things i use.

quick note.. soom edu ips block the actual level1.gz mirror, think its beacuse bluetack are using free hosts atm.

---

