---
title: "Sound Problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by DrkVagrant on 2008-04-16
So i just got sound to work, and it was working fine. Now all of the sudden i'm getting a lout ringing out of one speaker and it plays fine in the other. Any suggestions?

---

### Post by xeth_delta on 2008-04-16
Can you please provide more information on your system?

Brand and model.
Sound card:
```
sudo lshw -C sound
cat /proc/asound/card0/codec#0 | grep -i codec
```

---

