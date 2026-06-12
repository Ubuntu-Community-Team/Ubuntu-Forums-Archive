---
title: "how to use hddtemp"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2007-01-10
I used Synaptic to find a SMART monitoring tool called HDDtemp. I got that and smartmontools but can't find them once they're installed. How do I use this hddtemp and is there a way to have it appear as an icon that I can click to check the temps whenever I need to?

---

### Post by play0r on 2007-01-10
you have to use it from the terminal.

```
sudo hddtemp /dev/hda
```

will check the temps on your first ata drive. if you want to check all of your hard drives just add them to the same line.

ez,
play0r

---

### Post by atarileaf on 2007-01-10
Ok, got it. I was hoping for something that sat in the system tray so it could be checked regularly.

---

### Post by autocrosser on 2007-01-10
there are a couple of applets that use it & gkrellm uses it. you can also setup conky with it.

---

### Post by atarileaf on 2007-01-10
> **autocrosser said:**
> there are a couple of applets that use it & gkrellm uses it. you can also setup conky with it.

Thanks. I'll try that Conky program. I also tried desklets but the monitor kept reporting 0 degrees. :-k

---

