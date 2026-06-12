---
title: "How do I become the &quot;owner&quot;"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Toroxor on 2007-10-22
When I was trying to change my screen saver I noticed something strange, apparently, I do not have permission to change certain things because im not the owner.  Instead, something called root is, and i cant seem to change this in users and groups, anyone know how to make a certain user the 'owner'?

---

### Post by Pumalite on 2007-10-22
[http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)

---

### Post by mali2297 on 2007-10-22
> **Toroxor said:**
> When I was trying to change my screen saver I noticed something strange, apparently, I do not have permission to change certain things because im not the owner.  Instead, something called root is, and i cant seem to change this in users and groups, anyone know how to make a certain user the 'owner'?

If you have files in your home folder that you don't "own", change the ownership with:
```

chown yourusername:yourusername filename

```
(... in the terminal.)

But otherwise, you should probably let root remain the owner. The user root is also called superuser. You can take the role of root by typing sudo or gksudo in front of the command that you want to execute. If you want to edit files that is owned by root, just type:
```

gksudo gedit filename

```

For more information, see
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

