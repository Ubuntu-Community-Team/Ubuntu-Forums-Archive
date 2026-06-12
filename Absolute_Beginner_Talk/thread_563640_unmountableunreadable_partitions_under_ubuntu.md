---
title: "unmountable/unreadable partitions under ubuntu"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by banda on 2007-09-30
[IMG]http://i23.tinypic.com/1zdpw1c.jpg[/IMG]
thats how my partition table looks now.

i am running gutsy beta from the last couple of days. ihave all my data stored on hda2 and hda3 and have my windows install(which is no longer working) on hda5. till a few hours back i was able to access hda2&3 without any problem although hda5 has never been showing up in ubuntu. but somehow i can no longer access my main storage partitions now... have i lost the data?????
help

---

### Post by joncheyne on 2007-09-30
> **banda said:**
>  have i lost the data?????
help

Probably not :-) 

If you go to Places | Computer what do you see?

---

### Post by banda on 2007-09-30
i see only cd drives , floppy drive and the linux root

---

### Post by joncheyne on 2007-09-30
And just to check .. do you still have ntfs-3g installed? (unless things have changed under gutsy, I am still feisty))

---

### Post by banda on 2007-09-30
on gutsy i don't need to install that.. ntfs write access was also available

---

### Post by joncheyne on 2007-09-30
> **banda said:**
> on gutsy i don't need to install that.. ntfs write access was also available

What about fstab - anything in there that's relevant?

where were they mounting before - /media?

---

