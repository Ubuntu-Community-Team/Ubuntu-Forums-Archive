---
title: "how to change owner back to root"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ralph juncel on 2007-03-19
hi to all,

   I'm new to ubuntu linux.  I have accidentally changed the ownership of the /var folder to ralph my own user account. I would like to change it back to root using chown root var/ but it just displays operation not permitted. How to do I fix this?
Please help. tnx

---

### Post by simonn on 2007-03-19
```

$ sudo chown root:root /var

```

---

### Post by nickburns on 2007-03-19
sudo chown root:root -R /var

you may need the -R to change it recursively.

---

