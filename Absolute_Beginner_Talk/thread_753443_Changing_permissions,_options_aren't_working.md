---
title: "Changing permissions, options aren't working"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by dustoashes on 2008-04-12
I'm using Ubuntu 7.10 and I'm trying to include in Apache2.conf this:

I've tried:

```
sudo vi /etc/apache2/apache2.conf
```

But I don't know how to edit this in the terminal, where it opens... so I opened the file in text editor and tried inserting this:

```
Include /etc/phpmyadmin/apache.conf
```

But it just won't let me. I've added myself into the root group and I've tried this:

```
sudo chmod +rwx /etc/apache2/apache2.conf
```

But I still can't write in it, still says I'm not the owner so I can't! Help please?

---

### Post by hyper_ch on 2008-04-12
try:

```

sudo nano /etc/apache2/apache2.conf

```

nano is simpler to use

---

### Post by dustoashes on 2008-04-12
Thank you, it works like a charm. :)

---

