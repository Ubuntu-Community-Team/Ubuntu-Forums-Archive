---
title: "Another Grub Problem .... #22"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by fmen on 2007-06-21
This one's a doozy!

How do you clear the mbr of Grub (error 22) on a laptop without a floppy drive or cd drive?

Boot goes as far as.....

[B]GRUB loading stage1.5.

GRUB loading, please wait...
Error 22[/B]

Thanks for any suggestions.:sad:

---

### Post by alienexplorers on 2007-06-21
Try this.  Don't know if it will work this way.
Enter Terminal and enter sudo grub.
Enter > find /boot/grub/stage1
you will get an output such as (hd#,#)
Enter> root (hd#,#)
Enter> setup (hd#)
exit grub editor
reboot system.

---

### Post by fmen on 2007-06-21
Oh, how I wish I could get to a prompt that would allow me to enter anything at all.

Booting the laptop only gets me as far as the Error 22 message.

Thanks for the reply, though.

---

### Post by alienexplorers on 2007-06-22
How did you get ubuntu loaded in the first place?

---

### Post by fmen on 2007-06-22
> **alienexplorers said:**
> How did you get ubuntu loaded in the first place?

Good question!

It wasn't easy, but there are ways.....

[http://www.mepislovers.org/forums/showthread.php?t=7909&highlight=installing+floppy](http://www.mepislovers.org/forums/showthread.php?t=7909&highlight=installing+floppy)


I did a dumb thing, though. The installation proved to be too slow so I reformatted the drive before getting rid of GRUB. Now I am stuck with it forever. I was hoping to recover the drive.

---

### Post by BLTicklemonster on 2007-06-26
I hope this is right. I'm using hda3, which is on hd1, hd0,2, therefore:
```

grub> root (hd0,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd1)"...  18 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+18 p (hd0,2)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> root(0,2)
```

I hope that's right.

---

### Post by BLTicklemonster on 2007-07-09
Oops, it started doing it again, so I did this again...
```

grub> root (hd0,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd1)"...  18 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+18 p (hd0,2)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> root(0,2)

Error 27: Unrecognized command


```

Now what?

---

