---
title: "[SOLVED] permissions"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by frmach on 2007-11-18
How can I change permissions on a file when "root" is the owner?

---

### Post by overdrank on 2007-11-18
> **frmach said:**
> How can I change permissions on a file when "root" is the owner?

Hi and welcome you can use the keys alt, F2  and enter ```
gksudo nautilus
``` This will let you access the file as root. This link may help also
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LaRoza on 2007-11-18
> **frmach said:**
> How can I change permissions on a file when "root" is the owner?

For the command way:

```

sudo chmod <options> <file>

```

```

sudo chown <user>:<group> <file>

```

---

