---
title: "Does an extracted tarball need to be somewhere special to install?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by DaveIsInTrouble on 2007-02-03
I'm trying to install ruby-1.8.5, and I put it in my home directory after extracting it. I went into the directory, did ./configure, make, and then make install like the readme said, and no error messages popped up, but I still can't find evidence it installed correctly!

---

### Post by taurus on 2007-02-03
Are you sure you didn't get any error message when you ran "make install"?  That command usually installs stuff to /usr/local/bin and/or /usr/local/lib and you don't have permission to write to any of those directories.

Try

```
./configure
make
sudo make install
```

---

### Post by DaveIsInTrouble on 2007-02-03
Oh yeah, I used sudo make install, sorry, but yeah, it installed like I've seen everything else install...

---

### Post by taurus on 2007-02-03
And where did it say it installed to?  Maybe you just need to reboot.

---

### Post by DaveIsInTrouble on 2007-02-03
Okay, I rebooted and it looks that fixed it. :)

Thank you :D

---

