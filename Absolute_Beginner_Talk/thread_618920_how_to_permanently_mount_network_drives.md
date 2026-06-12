---
title: "how to permanently mount network drives"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-11-20
I've done this before when using Edgy, but now the same commands don't seem to work in Gutsy.  I want to be able to mount 3 network drives with full write permissions.  Maybe I am doing something wrong, I don't know.  I know that I should be putting a line in my FSTAB file, but the one I used doesn't seem to work with full write permissions.

```
//Server/ShareName     /mnt/ShareName     smbfs     defaults,uid=<username>,username=xxxxxx,password=xxxxxx     0     0
```

I tried putting this in my FSTAB but when I reboot the drives are not mounted.  Anyone know what I am doing wrong?

---

### Post by jken146 on 2007-11-21
I believe you need to create the /mnt/ShareName directory first.

---

### Post by kc5hwb on 2007-11-22
I did that already.

I tried it again and it seemed to work this time.  I tried it a few weeks back and couldn't get it to work at all.  Maybe I was doing something wrong, who knows.  But thanks for the reply.

---

