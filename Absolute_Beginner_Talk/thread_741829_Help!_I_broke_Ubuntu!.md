---
title: "Help! I broke Ubuntu!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2008-04-01
I currently can' boot into ubuntu because I accidently deleted the bash/sh directory! help greatly appreciated.

---

### Post by kellemes on 2008-04-01
> **metalpancake said:**
> I currently can' boot into ubuntu because I accidently deleted the bash/sh directory! help greatly appreciated.

What's a bash/sh directory?
Can you please be more specific?

---

### Post by metalpancake on 2008-04-01
```
init: Unable to execute "bin/sh" for rcs: no such file or directory.
``` 
Sorry, got the names confused. So I actually accidently removed bin/sh.

---

### Post by ByteJuggler on 2008-04-01
Boot up with your LiveCD, mount your installation, and restore /bin/sh back onto your installation from the LiveCD environment.  (Note, usually /bin/sh is a symbolic link to another physical file anyway, so putting "/bin/sh" back likely means linking it again from the appropriate file (typically /bin/dash), rather than copying it from the liveCD as you might think.) To link /bin/sh to /bin/dash do from a command prompt (if your installation is mounted under /mnt/target):

```

cd /mnt/target/bin
sudo ln -s dash sh

```

---

### Post by metalpancake on 2008-04-01
ok, thank you.

---

### Post by Bushfire on 2008-04-01
Just out of curiosity, *why* did you delete /bin/sh?

---

### Post by metalpancake on 2008-04-01
It was in an online tutorial for compiling a program. I think I typed the command wrong because I doubt that deleting bin/sh was the intended outcome.:lolflag:

---

### Post by Bushfire on 2008-04-01
> **metalpancake said:**
> It was in an online tutorial for compiling a program. I think I typed the command wrong because I doubt that deleting bin/sh was the intended outcome.:lolflag:

Unless the program had unlink("/bin/sh") in there somewhere, no, I think you're right. :)

---

### Post by metalpancake on 2008-04-01
i remember that the command has sudo rm in it somewhere, so I think that that was the culprit. Why it asked me to do this I don't know.

---

### Post by metalpancake on 2008-04-01
Can you boot off a Ubuntu iso off a dvd rather than a cd? That's all I have at the moment.:(

---

### Post by ByteJuggler on 2008-04-01
> **metalpancake said:**
> Can you boot off a Ubuntu iso off a dvd rather than a cd? That's all I have at the moment.:(

Yes.

---

### Post by metalpancake on 2008-04-01
That's weird. because when I tried, it just went straight to the grub loader. any ways to fix this?

---

### Post by ByteJuggler on 2008-04-01
Hmmm, well, at the risk of asking the obvious, are you sure your boot order in the BIOS is set to allow booting from CD/DVD first?   (I've burned the Ubuntu ISO to DVD's many times and booted them, so it's definitely possible...)

---

### Post by metalpancake on 2008-04-01
I didn't think of that!:lolflag:

---

