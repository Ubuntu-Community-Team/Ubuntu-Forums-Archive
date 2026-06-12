---
title: "Mounting from a pen drive to a different location ?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by shadowphoenix on 2007-01-09
i want to know how do i mount from a pen drive to a different location in home folder.I keep on trying but it seems not to work.I can open the contain inside the pen drive but i can't seem to move it to a different location.Do anyone here know what is the command ?Thank you in advance

---

### Post by Ben Sprinkle on 2007-01-09
Depends, it should be sda1, sda2 or what have you.
```

sudo umount <place-already-mounted>

```
Then mount it:
```

sudo mount /dev/sda1 /home/yourfolder

```
Tell me if you have problems.

---

