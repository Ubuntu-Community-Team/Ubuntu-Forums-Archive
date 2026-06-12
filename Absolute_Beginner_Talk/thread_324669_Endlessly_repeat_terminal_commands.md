---
title: "Endlessly repeat terminal commands"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Famicommie on 2006-12-24
I was wondering if there was any way to have a command in terminal repeat itself until I ctrl+c it. I'd even appreciate knowing if it were only possible by a script. Right now I'm doing a silly little experiment, but I had to cut and paste the command 100 times into a .sh file because I couldn't find any better method. Anyone know?

---

### Post by po0f on 2006-12-24
Famicommie,

```
[FONT="Courier New"]#!/usr/bin/env python
while True:
    print "spam"[/FONT]
```

I forget exactly how to do an infinite loop in Bash.

[EDIT]

```
[FONT="Courier New"]#!/bin/bash

while [[ 1 ]]; do
    echo -e "spam"
done[/FONT]
```

---

### Post by Famicommie on 2006-12-24
Thanks po0f. Worked like a charm!

---

