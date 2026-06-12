---
title: "Could not install from source"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by sundar22in on 2008-01-17
I could not install from source.

I tried running and it says it could not execute gcc successfully.

Any pointers for installing a app from source?

~ Sundar ~

---

### Post by kpkeerthi on 2008-01-17
What are you trying to install?

Install the build-essential packages to get the compilers and stuff.

```

sudo aptitude install build-essential

```

---

### Post by sundar22in on 2008-01-17
I do not have internet connection in my Ubuntu machine? How do I go about this?

---

### Post by kpkeerthi on 2008-01-17
Some apps need kernel-headers
```

sudo aptitude install linux-headers-`uname -r`

```

**Note the reverse quotes**

---

### Post by sundar22in on 2008-01-17
I was trying to install VLC player.

---

### Post by kpkeerthi on 2008-01-17
> I do not have internet connection in my Ubuntu machine? How do I go about this?
I think you are pretty much stuck. You can purchase [Ubuntu Repository DVD]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html") if you could afford. [More...]("http://www.google.com/search?q=ubuntu+repository+DVD")

---

