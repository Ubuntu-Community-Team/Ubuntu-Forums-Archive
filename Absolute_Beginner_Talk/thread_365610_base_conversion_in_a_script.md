---
title: "base conversion in a script"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-19
How can I do base conversions in a bash script? i tried using bc but I can't echo the result...

---

### Post by IYY on 2007-02-19
Post the BC script you wrote, and I'll tell you how to echo it back.

---

### Post by syalam on 2007-02-20
Well I guess I can't even get it in the script, how can I execute BC in 1 line?

I tried

ibase=16;obase=10;F | bc

Is that correct?

---

### Post by conrad.irwin on 2008-01-16
You should set obase before ibase, otherwise you have to give obase in the new ibase - which can be confusing.

```
echo "obase: 10; ibase 16; FF" | bc -q  
```

Incidentally does anyone know a tool for conversion between arbitrary bases?

---

