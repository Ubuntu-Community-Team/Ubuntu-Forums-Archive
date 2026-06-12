---
title: "power off in a command prompt"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Liolikas on 2006-11-11
How I can power off my laptop in command prompt?

---

### Post by Liolikas on 2006-11-11
Thx anyway I found answer on myself :D 

**poweroff [-n] [-w] [-d] [-f] [-i] [-h]**

---

### Post by findus on 2006-11-11
You can also use the init command

To power off, just type

```
init 0
```

---

### Post by s_h_a_d_o_w_s on 2006-11-11
or sudo reboot to reboot. I find it'smore "geeky" and it makes my friends think im a hacker. Lol.

---

### Post by digby on 2006-11-11
You can also use the shutdown command w/ -r for reboot or -h (halt) for powerdown

```
sudo shutdown -h now
```

the now can also be replaced with +x where x is the number of minutes to wait before shutting down.

---

