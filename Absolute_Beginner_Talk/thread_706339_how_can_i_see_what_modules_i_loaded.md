---
title: "how can i see what modules i loaded"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by rob1101 on 2008-02-24
i need to look and see what modules have loaded on my  machine specifically the one for the NIC card.  and can i look at them from a live CD?

---

### Post by Cypher on 2008-02-24
```

/sbin/lsmod

```
Will list all of the Kernel modules..

---

### Post by mkoehler on 2008-02-24
Yes, you can look at them from a live cd with the lsmod command, as stated above.

---

