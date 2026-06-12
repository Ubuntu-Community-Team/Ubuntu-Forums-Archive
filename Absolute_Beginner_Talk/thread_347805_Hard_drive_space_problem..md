---
title: "Hard drive space problem."
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by drascus on 2007-01-27
I have formatted my hard drive quite a few times. I have noticed over that period that my computer has gone from 60 gig down to 52 gig. Is this a result of formatting it? is there a way to format it and reclaim that space which I have lost?

---

### Post by taurus on 2007-01-27
What filesystem did you format it to?

---

### Post by drascus on 2007-01-27
umm whatever Ubuntu's default does when you erase the disk and install. I think thats FAT right?

---

### Post by taurus on 2007-01-27
It should be ext3.  

```
sudo fdisk -l
```

---

