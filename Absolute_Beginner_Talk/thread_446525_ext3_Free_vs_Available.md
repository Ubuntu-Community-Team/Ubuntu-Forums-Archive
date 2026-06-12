---
title: "ext3: Free vs Available?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Klargodut on 2007-05-17
As you see in the screenshot, the free and available sizes of my ext3 partition differs with about 1 GB. Why is that?

---

### Post by k1001001 on 2007-05-17
The 1 GB in difference may be due to a swap partition/file.

---

### Post by Klargodut on 2007-05-17
During install, I set the swap partition to be somewhere around 500 MB, which is confirmed by this command:

```

emil@linux-laptop:~/Musik$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       498004  33176   -1

```

But that doesn't explain the other 500 MB's...

---

### Post by Magnes on 2007-05-17
[http://ubuntuforums.org/showthread.php?p=2645493](http://ubuntuforums.org/showthread.php?p=2645493) - read this thread

---

### Post by Klargodut on 2007-05-17
Ah, thank you! I will remember this in case I run short of space.

---

### Post by Klargodut on 2007-05-18
I decided I didn't want the root user to have 1 GiB as a backup in case something went wrong, so i reduced it to about 100 MiB by using:

```

emil@linux-laptop:~$ sudo tune2fs -r 26000 /dev/hda3
tune2fs 1.40-WIP (14-Nov-2006)
Setting reserved blocks count to 26000

```

---

