---
title: "Kubuntu 7.04 - How do you save in Konsole?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by chager on 2007-08-20
Kubuntu 7.04 - How do you save in Konsole?

I'm trying to configure Wvdial for my modem.  It recognizes my modem, but when I inter the info for my ISP and try to save it does not save like in Ubuntu.

I use:

Ctrl – o (save)
Ctrl – x (exit)

Are there other commands?  I’ve tried as root and regular no luck.

Thanks

---

### Post by Happy_Man on 2007-08-20
Are you talking about using Nano in Konsole? If so, I'm not sure whether Ctrl-o works. Ctrl-x should ask if you want to save, though.

---

### Post by chager on 2007-08-20
Yes I used nano.

$ sudo nano /etc/wvdial.conf

I'll try ctrl-x.  I got the prompt to save and I said Yes, but it didn't save?

Should I not use nano?

---

### Post by Happy_Man on 2007-08-20
You could always use something graphical. like Kate.... ```
kdesu kate /etc/wvdial.conf
```

---

### Post by g2g591 on 2007-08-20
to exit (and save) use ctrl+x then press y (for yes) and hit enter twice

---

### Post by chager on 2007-08-21
Happy_Man, G2g591

Thanks it worked

---

