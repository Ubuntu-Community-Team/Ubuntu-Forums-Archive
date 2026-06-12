---
title: "$home"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-07-12
Ubuntu crashed and after I rebooted this message appeared:
```

$HOME./drmc does not exists, allow read permissions of 644...

```

Or something like that. How do I fix this?

-Ryan

---

### Post by Kilz on 2006-07-12
> **Ryan H said:**
> Ubuntu crashed and after I rebooted this message appeared:
```

$HOME./drmc does not exists, allow read permissions of 644...

```

Or something like that. How do I fix this?

-Ryan

I think I have had this error befor. You may have changed the chmod on your home directory. Change <username> to your username.
```
sudo chmod 644 /home/<username>/.drmc
``` 
should stop the error and alow you to boot. You may have to change other permissions once you get it to boot

---

### Post by Ryan H on 2006-07-12
```
chmod: cannot access `/home/ryan/.drmc': No such file or directory
```

Didn't work?

-Ryan

---

### Post by echo $USER on 2006-07-12
try this > sudo chmod -R 744 /home/ryan

---

