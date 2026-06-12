---
title: "Create custom launcher"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by helino on 2007-10-14
Hi, I need to create a launcher, or script, that does the following:

1. First becomes su
2. then do the following in the terminal: 
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss]
```
3. then do this;
```
cd /usr/local/games/utr/
```
4. And finally does this:
```
./ioUrbanTerror.i386
```

How do you do this?

Thx for all your help

---

### Post by Abild on 2007-10-14
Save
```

#!/bin/bash
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
/usr/local/games/utr/ioUrbanTerror.i386

```
in a file.
Make the file executable by running chmod +x filename
and then you should be able to run it using ./filename

---

### Post by helino on 2007-10-14
What file format should I save the file as, .run? 

Thank you for your help

---

### Post by Palmyra on 2007-10-14
> **helino said:**
> What file format should I save the file as, .run? 

Thank you for your help

I think you should save it as .sh (shell file).  Give it a try.

---

### Post by helino on 2007-10-15
Thanks, it works perfect!

---

