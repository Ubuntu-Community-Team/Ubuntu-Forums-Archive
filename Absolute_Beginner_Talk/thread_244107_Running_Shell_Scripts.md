---
title: "Running Shell Scripts"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by themusicwave on 2006-08-25
I am trying to instal.
l Sun Studio from a shellscript.  This apparently should be really easy, but I cannot get it to work.

I read soewhere to try sudo ./shellname  but that failed

Can someone give me some basic step by step instructions for this?  I know nothing about these scripts.

---

### Post by Bachstelze on 2006-08-25
./filename is the way to go but before, you need to make the file executable with 

```
sudo chmod +x filename
```

In some cases, ./filename won't work, then use sh filename :)

---

### Post by themusicwave on 2006-08-25
I forgot about the permissions thing.

Thank you I ws going nutz, had no idea why ./ wouldn't work.  Well this is resolved!

---

