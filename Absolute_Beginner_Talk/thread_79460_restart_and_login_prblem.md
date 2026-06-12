---
title: "restart and login prblem"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by andy81 on 2005-10-20
hi, i know pretty much nothing about ubuntuyet so i need alittle help.

I dont know what i did, but now, when I got to logon, and restart, instead of resarting automaticly, or startng direct into ubuntu, i get out into a terminal.  I can get back in by typing "startx" but i really doing want to login or out to the terminal.  how do i fix this?

Thanks

---

### Post by Kyral on 2005-10-20
[quote=andy81]hi, i know pretty much nothing about ubuntuyet so i need alittle help.

I dont know what i did, but now, when I got to logon, and restart, instead of resarting automaticly, or startng direct into ubuntu, i get out into a terminal. I can get back in by typing "startx" but i really doing want to login or out to the terminal. how do i fix this?

Thanks[/quote]

It sounds like you stopped GDM. Try going back to your terminal (logout first so X isn't running) and do this

```
sudo /etc/init.d/gdm start
```

---

