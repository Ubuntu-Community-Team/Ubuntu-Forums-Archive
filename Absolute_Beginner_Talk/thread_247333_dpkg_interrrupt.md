---
title: "dpkg interrrupt"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by DougieFresh4U on 2006-08-30
Here I go again. I am trying to un-install wine as it fails to load all the way. machine locked up on in-instal and now i can not get into pkge manager I get error- E:dpkg was interrupted, you must manually run dpkg-configure -a and when I do that it says command not found.I can not install or un-install wine with any sccess. some one please help](*,)

---

### Post by Metacarpal on 2006-08-30
Just type in```
sudo dpkg-configure -a
```in the Terminal.

I had the same thing happen after I had to abort an installation.  Run that configure and it should sort itself right out.

---

### Post by jdong on 2006-08-30
The actual command, if you read the message carefully, is

```

dpkg --configure -a

```

Of course, you need sudo in front of it.

---

### Post by Metacarpal on 2006-08-30
> **jdong said:**
> The actual command, if you read the message carefully, is

```

dpkg --configure -a

```

Of course, you need sudo in front of it.

Thanks, jdong - missed that bit. ](*,)

---

