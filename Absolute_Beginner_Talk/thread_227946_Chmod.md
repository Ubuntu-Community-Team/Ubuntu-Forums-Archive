---
title: "Chmod"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by iambill on 2006-08-02
Hey all.  I know that chmod can change the permissioins of individual files.  On another distro I copied my .fvwm folder to another partition (using root) before switching to ubuntu.  After copying it back to ~/ I need to use sudo to change the config files and such.  My question is how do i chmod to change the permissions of the entire contents of .fvwm folder(and all of its sub folders) so that the user has the proper permissions again?

Thanks in advance.

---

### Post by rmjb on 2006-08-02
Use the -R switch to chmod recursively.

For example sudo chmod -R 600 .fvwm

Hope this helps,
- rmjb

---

### Post by cstudent on 2006-08-02
To change owner:
```

sudo chown -R username:username /folderpath/

```
To change permissions:
```

sudo chmod -R 755 /folderpath/

```


Edit: Had a brain fart. Had the two commands mixed and combined. I don't think that would work.

---

