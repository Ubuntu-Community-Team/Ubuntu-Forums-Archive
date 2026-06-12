---
title: "mounting floppy drive"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by kcampbell26 on 2006-02-08
Can anyone explain how to get ubuntu to mount my floppy drive?  Oddly enough, it will format a disk with no problems but refuses to mount the drive to read or write a disk. Thanks

---

### Post by TrendyDark on 2006-02-08
That's weird, usually floppy drives have no problems with Linux, seeing how a floppy drive is quickly becoming a legacy feature.

---

### Post by CookieOrc on 2006-02-08
If you want this will take a while, but it will get the job done. go to [http://www.tuxmagazine.com/](http://www.tuxmagazine.com/) Download the latest version and open the pdf. The fist question in Mingos Q&A answers that question.

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=kcampbell26]Can anyone explain how to get ubuntu to mount my floppy drive?  Oddly enough, it will format a disk with no problems but refuses to mount the drive to read or write a disk. Thanks[/QUOTE]
Try
```

$ pmount /dev/fd0

```
in a terminal.

---

