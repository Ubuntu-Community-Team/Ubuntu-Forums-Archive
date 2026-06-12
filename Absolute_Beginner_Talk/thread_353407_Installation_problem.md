---
title: "Installation problem"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by antiwindows798 on 2007-02-04
I tried to install a problem, doing this:

```
# chmod +x *binfile*
```

And this

```
# . *binfile*
```

And that produces the following message:

```
          The launcher "bash" 
          is not executable for the current user.  Please give 
          execute permission for the current user before 
          attempting to launch the installer.
```

Any ideas how to fix this?

---

### Post by antiwindows798 on 2007-02-04
BTW, I also tried doing that as root, doesn't work either.

---

### Post by shareMenaPeace on 2007-02-04
Maybe

chown username /path/to/file ?

---

### Post by antiwindows798 on 2007-02-05
Nope, doesn't work either.

---

### Post by antiwindows798 on 2007-02-06
Anyone?

---

