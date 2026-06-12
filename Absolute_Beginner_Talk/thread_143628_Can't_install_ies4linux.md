---
title: "Can't install ies4linux"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Peter Mount on 2006-03-12
Hello

I've tried to install ies4linux on Ubuntu 5.10 as per instructions at:

[http://ubuntuforums.org/showthread.php?t=132508&highlight=ies4linux+terminal](http://ubuntuforums.org/showthread.php?t=132508&highlight=ies4linux+terminal)

But when I try to run the "ies4linux" shell script (by clicking on it) in the terminal the terminal just appears for a split second and it dissapears again. What should I do?

Thanks

---

### Post by taurus on 2006-03-12
There is no error message at all when it terminated itself!!!  It's kind of hard to diagnose it without knowing the error...

---

### Post by aysiu on 2006-03-12
Follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then ```
sudo apt-get update
sudo apt-get install wine cabextract
```

---

