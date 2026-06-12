---
title: "Problem when trying to resize a partition"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by sinsen on 2006-05-18
Hello!

I have tried following various instructions to set up a dual boot installation.

When entering the partitioning menu, I choose to manually set up a partition, I choose my main (windows, ntfs) partition, and choose to resize it.

I set the new size to 40.0 GB, and, nothing happens, I just pop back to the menu where I am supposed to choose a disk or partiton.

Any ideas of what I am doing wrong?

Thank you.

---

### Post by skinnygmg on 2006-05-18
how big is your HDD?

---

### Post by sinsen on 2006-05-18
160 GB, 126 GB of it is free.

---

### Post by johnc4510 on 2006-05-18
The easiest way to change or set a new partition is with Gparted live cd, you can google for this. Download and burn it to cd, then boot the system from the gparted live cd. Redo the Partions and exit.

---

### Post by Klaidas on 2006-05-18
Hopes this helps if you try an alternative partitioning (like using GParted): [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by sinsen on 2006-05-18
Great, thank you all, I'll try using GParted.

I'll be back, crying some more, if it does not work.

---

### Post by Klaidas on 2006-05-18
Just remember to back-up everything!

---

### Post by sinsen on 2006-05-18
No worries, got all important stuff on a separate disk.

No luck with Gparted, I'll try to defragment my disk again using a nice commercial defragmenter and see if that helps...

---

### Post by Klaidas on 2006-05-18
Does it give any errors or is it the same as live cd partitioning?

---

### Post by sinsen on 2006-05-18
No help partitioning either.

It gives me an error message, but "Error when trying to resize x to x" does not tell me much.

(I would have given you the complete message, but I only have the one computer at home right now.)

---

### Post by Ecthelion on 2006-05-18
You can also try qtparted.
I had trouble with Gparted (some segmentation error) and since the live-cd failed too i tried qtparted
i've done a lot of resizing with it and it works fine.

Only thing: I don't know if it is normal but you can only change the ending blok with it. There is no way changing the start blok with qtparted (it is set grey so you can't change it)

---

### Post by sinsen on 2006-05-18
Hooray, a quick chkdsk /f fixed it, wich is strange, as a plain chkdsk reported no problems.

Anyway, now all is fine, except that i get a "no screen found" error when loading X.

But, I am pretty sure that solving that problem is just a couple of googles away.

Thank you again.

---

