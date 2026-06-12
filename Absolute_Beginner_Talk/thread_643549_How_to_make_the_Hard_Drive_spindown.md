---
title: "How to make the Hard Drive spindown"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-12-17
I am wondering how to make the hard drive spin down as it seems it is spinning continuously.  How do I do this?  I had to set the hdparm to 254 to stop high load count cycles, does this have an effect?  Could the responses go into detail on how to do this I am still trying to learn linux.  Any suggestions are greatly appreciated!

---

### Post by RomeReactor on 2007-12-17
Hi. In case you haven't read it, [this Ubuntu wiki entry]("https://wiki.ubuntu.com/DanielHahler/Bug59695") has a very good explanation. In short, I think you can set hdparm to 255, though the author states that it doesn't work on all hard drives.

---

### Post by hockeyfighter09 on 2007-12-17
I found that if i set the hdparm to 255 that the cycle count increases as fast as it did before I set it to 254.  Thanks for finding this article I will give it a look and see if I can figure this out.:)

---

