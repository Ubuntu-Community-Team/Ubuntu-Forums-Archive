---
title: "Cannot install build-essential"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by paolo17 on 2006-11-27
hi im trying to install build-essentials using "sudo apt-get install build-essentials" but i cannot install it after showing some text like "building dependencies blah blah" it ends up "E:cannot find {something..}" i tried inserting my ubuntu cd but still the same thing appears. what do i need to do? im trying to install a software from source and i can't since there is no make and other stuff needed. thanks in advance to those who will help me.

---

### Post by LLRNR on 2006-11-27
Try... **build-essential** i.e. without the trailing "s" :) I guess that should work.

LLRNR

---

### Post by paolo17 on 2006-11-27
wow, nice one, thanks man!

---

### Post by Neil Lundy on 2007-01-17
Hi Guys,

What if you want to install the build essential without a current internet connection. Any help would be much appreciated.

Thanks Neil

---

### Post by taurus on 2007-01-17
It's on the CD that you installed Ubuntu.  Insert the CD into a drive.  Open a terminal and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

