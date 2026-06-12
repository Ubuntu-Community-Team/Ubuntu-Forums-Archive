---
title: "mpg to 3gp or mp4"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-24
how do u convert mpg to 3gp or mp4
plz help me out

---

### Post by jackmc on 2007-06-24
I use zamzar.com

I find it easier than trying to set it ip in Feisty, and they are quick too :)

---

### Post by zerobinary on 2007-06-24
i mean my interent speed sux so can u teach me how to install a app on ubuntu instead
plz come back and help

---

### Post by rootkit on 2008-01-31
have a look at my tools: [http://ubuntuforums.org/showthread.php?t=684197](http://ubuntuforums.org/showthread.php?t=684197)

---

### Post by harold4 on 2008-01-31
```

!/bin/bash
ffmpeg -i $1 -f mp4 -acodec mp2 `pwd`/$1.mp4

```

---

### Post by PinkFloyd102489 on 2008-01-31
You could use ffmpeg on the command line.


```

sudo ffmpeg -i file1.mpg file2.3gp

```


EDIT: Sniped. :-(

---

