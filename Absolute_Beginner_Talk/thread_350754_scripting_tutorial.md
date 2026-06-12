---
title: "scripting tutorial?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-02-01
anyone know any good script tutorials for the gnome terminal?

i keep finding bash tutorial and the scripts always give me errors.

i just want a loop that runs 100 times.


thanks

---

### Post by kelbizzle on 2007-02-01
[http://www.cyberciti.biz/nixcraft/linux/docs/uniqlinuxfeatures/lsst/](http://www.cyberciti.biz/nixcraft/linux/docs/uniqlinuxfeatures/lsst/)

---

### Post by ardchoille42 on 2007-02-01
> **jinxjinx said:**
> anyone know any good script tutorials for the gnome terminal?

i keep finding bash tutorial and the scripts always give me errors.

i just want a loop that runs 100 times.


thanks

```

#!/bin/bash
for ((a=0;a<100;a++))
do echo $a
done


```

One of my favourite sites had always been: [http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)
Couple of good bash guides there.

---

### Post by jinxjinx on 2007-02-01
when i try to run you script i get this:

ten.sh: 2: Syntax error: Bad for loop variable

---

### Post by NESFreak on 2007-02-01
> **jinxjinx said:**
> when i try to run you script i get this:

ten.sh: 2: Syntax error: Bad for loop variable

how do you run it?
do you```
sh ./ten.sh
```
or```
bash ./ten.sh
```
or```
./ten.sh
```
because only the last two are supposed to work. The first one (sh) referrers to DASH. which is way less feature rich than BASH which causes the errors. (or well it does for me)

NESFreak

---

### Post by jinxjinx on 2007-02-01
thanks, that solved it.

---

