---
title: "K3b, cdrecord and user rights"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by lifeartist on 2006-07-18
Every time i start k3b or GNOME baker as regular user, i can't write to  a cd or dvd, and popup massge appears:" Can't open device...blah blah blah u do not have sufficient user privelgies" . Anyone can help?

---

### Post by taurus on 2006-07-18
Make sure you add yourself to group cdrom in /etc/group!  Open a terminal and type

```

sudo gedit /etc/group

```

---

### Post by lifeartist on 2006-07-18
I'm already added in cdrom group. I don't see whut's the problem.

---

### Post by k420 on 2006-07-18
well untill someone can help you can type in shell ```
sudo k3b
```

---

