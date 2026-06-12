---
title: "pipes with tcpdump"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by provisional_idiot on 2008-03-05
can't seem to figure out why ```
tcpdump -t -l -n | awk '/S/ { print $6 }' | sed 's/:/ /' 
```
doesn't, especially since ```
tcpdump -t -l -n | awk '/S/ { print $6 }' 
``` works just fine:

```

root@comp:~# tcpdump -t -l -n | awk '/S/ { print $6 }'
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
3878217877:3878217877(0)
615460754:615460754(0)
3901032956:3901032956(0)
647693530:647693530(0)
3895558697:3895558697(0)
636406252:636406252(0)
260 packets captured
260 packets received by filter
0 packets dropped by kernel

```

but with tcpdump -t -l -n | awk '/S/ { print $6 }' | sed 's/:/ /'  i get nothing


any help??

---

### Post by provisional_idiot on 2008-03-06
bump

---

