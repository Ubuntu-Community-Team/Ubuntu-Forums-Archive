---
title: "how can i find recycle bin using cmd line?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-05-15
Traditionally, if I do a rm to delete files it is gone. When i delete files off of Desktop (for ie) it still shows like on the Nautilius recycle bin.

how can i find the files sitting at that recycle bin using cmd line?

---

### Post by heimo on 2007-05-15
> **gotquestions said:**
> Traditionally, if I do a rm to delete files it is gone. When i delete files off of Desktop (for ie) it still shows like on the Nautilius recycle bin.

how can i find the files sitting at that recycle bin using cmd line?

I believe it's ~/.Trash or something similar (that is: dot Trash under your home directory)

EDIT: As we are on Beginner forum, let's make it easier:

```

cd ~/.Trash
ls -l
```

Or in nautilus, type / and then /home/yourusername/.Trash

---

