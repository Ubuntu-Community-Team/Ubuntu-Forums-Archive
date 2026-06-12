---
title: "Creating a symbolic link"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-05
To fix an error (maybe) I need to create a symbolic link, this is the error:

```
/etc/resovconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolveconf/run/resolv.conf
```

I tried this:

```
ln -s /etc/resolvconf/run/resolv.conf /etc/resolve.conf
```

and it says this:

```
ln: creating symbolic link '/etc/resolve.conf' to '/etc/resolvconf/run/resolv.conf': File exists
```

When I try the command which gives the error (or actually warning):

```
sudo /etc/init.d/networking restart
```

I get the same error again, what am I doing wrong?

Calv

---

### Post by Abstract on 2006-10-05
You need to remove or move /etc/resolvconf/run/resolv.conf before you can place a symbolic link in its place. I can't advise you if that is a good idea or not, but it should get it working.

---

### Post by calvinthomas on 2006-10-05
I gues I should wait for whether thats a good idea first! Thanks for the tip

Calv

---

