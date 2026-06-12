---
title: "Unraring parted (volumed) files."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Fataltragedy2 on 2007-03-18
Hello,

I can unrar a single file, but when unrar-ing files which have been split into volumes, the rar won't unrar. It'll rar only the part within and individual file but will not create the file from a series of .rar files. Can anyone help me with this? Thanks!

---

### Post by xopher on 2007-03-18
This should work just fine, as it works for me :)

```
unrar x filename000.rar
```

If it doesn't work, then tell us what rar you have installed.. ```
dpkg -l | grep rar
```

---

### Post by Kobalt on 2007-03-18
Did you install both rar and unrar packages ? 
Because I have and I can unrar parted archives from File Roller just fine...

---

### Post by Fataltragedy2 on 2007-03-18
Here's my version:

ii  unrar                                 3.5.4-0.1                            Unarchiver for .rar files (non-free version)

Also, I'm using the archiver, not File Roller? How do I use this File Roller thingy?

---

### Post by Kobalt on 2007-03-18
> **Fataltragedy2 said:**
> Also, I'm using the archiver, not File Roller? How do I use this File Roller thingy?
File Roller is the name of the archiver.
My question was do you have **both** rar and unrar packages installed ? Check in Synaptic if the rar package is available and installed ?
I'm not sure it's the reason you can't extract them directly but it worth checking...

---

### Post by Fataltragedy2 on 2007-03-18
I got it to work, Thanks!

---

