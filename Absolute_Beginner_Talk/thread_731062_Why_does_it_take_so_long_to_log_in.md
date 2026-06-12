---
title: "Why does it take so long to log in?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-03-21
It takes me about 20 seconds to boot, and 30 to log in.  Is there anything like bootchart for the login process so I can see what's taking it so long?

Thanks.

---

### Post by kellemes on 2008-03-21
> **Yes said:**
> It takes me about 20 seconds to boot, and 30 to log in.  Is there anything like bootchart for the login process so I can see what's taking it so long?

Thanks.

[http://www.bootchart.org/]("http://www.bootchart.org/")
```
sudo apt-get install bootchart
```

---

### Post by billgoldberg on 2008-03-21
> **Yes said:**
> It takes me about 20 seconds to boot, and 30 to log in.  Is there anything like bootchart for the login process so I can see what's taking it so long?

Thanks.

It has to load gnome/compiz after you log in (and some other services).

Go to "system -> preferences -> sessions" you can disable services to start on login, thus making starting faster.

---

