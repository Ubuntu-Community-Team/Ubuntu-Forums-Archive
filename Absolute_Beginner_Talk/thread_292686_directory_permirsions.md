---
title: "directory permirsions"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-11-04
why ain't i able to make the default download directory for firefox in /home/myname/download ? i tried but it just won't work. it gives an error message saying that it is a read only dir. i don't think i have to be root to be allowed to write there...

---

### Post by philippe_carlo on 2006-11-04
try the follwoing (replace myname with your login):
```

sudo chown -R myname:myname /home/myname/download
chmod -R 755 /home/myname/download

```

---

### Post by mendingo84 on 2006-11-04
it worked. thank you! but why did i have to change permissions? isn't /home/myname a read/write dir by default?

---

### Post by localuser on 2006-11-04
> **mendingo84 said:**
> it worked. thank you! but why did i have to change permissions? isn't /home/myname a read/write dir by default?

How did the download directory get created?

---

