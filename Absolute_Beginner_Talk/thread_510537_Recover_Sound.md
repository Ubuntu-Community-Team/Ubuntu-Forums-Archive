---
title: "Recover Sound"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by natman on 2007-07-26
Hi
( i have another post in relation to amarok, but i belive the problem is much bigger )

I was having problems with my laptop sound, and i used the following to help
> [http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+pavillion+sound](http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+pavillion+sound)
Ever since amarok has refused to start ( just opens and stalls, i cant click anything on it ), no other sound application works either, i have also booted up the previous kernels ( which used to work with sound every time ) and they no longer work either.
Is there any way to recover what i once had ( ie sound )?

---

### Post by Cappy on 2007-07-26
Try deleting .asound* in your home folder:
```
cd ~; rm .asound*
```

---

### Post by natman on 2007-07-27
Thanks you very much thats a relife! thank you!!

---

