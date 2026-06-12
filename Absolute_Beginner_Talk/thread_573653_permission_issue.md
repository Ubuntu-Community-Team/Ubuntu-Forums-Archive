---
title: "permission issue"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-11
I just installed Apache 2 and php 5.  every time i was to create a folder of file of move a fold or file into the /var/ww i need to do it through the command line with sud, i who can i prevent this?

---

### Post by om1 on 2007-10-11
press alt and F2 keys at the same time and type
```
gksudo nautilus
```
that will give you file browser with root privilege

---

### Post by RyanZec on 2007-10-11
it there a way to give a folder(in this case /var/www) write access to everyone?

---

### Post by om1 on 2007-10-11
press alt and F2 keys at the same time and type

```
gksudo nautilus
```

that will give you file browser with root privilege

go to /var/
right click >> properties >>permissions set it there

---

