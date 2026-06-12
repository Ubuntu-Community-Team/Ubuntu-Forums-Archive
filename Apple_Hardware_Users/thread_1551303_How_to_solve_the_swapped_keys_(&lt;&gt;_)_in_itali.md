---
title: "How to solve the swapped keys (&lt;&gt; \|) in italian keyboards"
date: 2010-08-12
forum: Apple Hardware Users
---

### Post by sfresta on 2010-08-12
This simple tutorial is refered to a macbook 4.1 Santarosa. The purpose is to invert the functions of the keycodes 94 and 49. Ensure that using the command **xmodmap -pke**, they are:

[I]keycode  49 = backslash bar backslash bar notsign brokenbar
keycode  94 = less greater less greater guillemotleft guillemotrigh[/I]

**1** - Edit (or create) the .Xmodmap present in your home directory:

```
nano ~/.*Xmodmap*
```**2** - Add the following lines:

```

keycode  94 = backslash bar backslash bar notsign brokenbar
keycode  49 = less greater less greater guillemotleft guillemotright

```**3** - Activate the changes:

```
 xmodmap ~/.*Xmodmap* 
```

---

