---
title: "how to check amount of RAM"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by zoffmann on 2007-05-29
Hello,

which linux commando can I use to check amount of available RAM?

thanks

---

### Post by YoG%*@ on 2007-05-29
hi 

the 'free' command might be what you're looking for.

hth
mux

---

### Post by zoffmann on 2007-05-29
Is there any command which shows total amount of RAM, and  CPU type, hd capacity ?

(the whole system configuration)

---

### Post by zoffmann on 2007-05-29
"free" worked 

thanks

---

### Post by YoG%*@ on 2007-05-29
you're welcome =)

for more information you could try
```

cat /proc/cpuinfo
cat /proc/meminfo
df -h

```

---

### Post by raul_ on 2007-05-29
or install hardinfo to get a complete system information, even benchmarks

---

### Post by arijarot on 2007-05-29
I know it's not a command line, but you can also see all this info graphically in system>administration>**system monitor**

---

