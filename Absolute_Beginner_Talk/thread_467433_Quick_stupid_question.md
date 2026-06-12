---
title: "Quick stupid question"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by rgraves22 on 2007-06-07
Is there a way to find out my system properties ( processor speed, RAM etc ) from the terminal?

---

### Post by jfinkels on 2007-06-07
> **rgraves22 said:**
> Is there a way to find out my system properties ( processor speed, RAM etc ) from the terminal?

You might try ```
sudo lshw
```

As there will be a lot of output, I would filter it through less:
```
sudo lshw | less
```

---

### Post by arochester on 2007-06-07
See "Find Hardware Specs (Details) on your Computer  " at [http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/](http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/)

---

### Post by yabbadabbadont on 2007-06-07
```
cat /proc/cpuinfo
cat /proc/meminfo

```

---

### Post by networkfu on 2007-06-07
processor:

cat /proc/cpuinfo

memory:

cat /proc/meminfo

other ones for example

cat /proc/version

---

### Post by Gagle on 2007-06-07
Yep,

memory : free

the lspci command also yields interesting results.

Precise your thoughts because everything can be done from the CLI .  :)

regards,

Gagle

---

### Post by Milos_SD on 2007-06-07
CPU info: cat /proc/cpuinfo
RAM: cat /proc/meminfo

For rest files look in the /proc/ directory.

---

