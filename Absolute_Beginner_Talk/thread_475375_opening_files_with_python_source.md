---
title: "opening files with python source?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by kiryo on 2007-06-16
found solution:
#!/bin/sh
ABCLOC='/home/kiryo/my_stuff/ohjelmat/LH-ABC_3.2.0/lh-abc.py'
PARAM="$*"
python "$ABCLOC" "$PARAM"
exit 0
thanx to a friend

---

