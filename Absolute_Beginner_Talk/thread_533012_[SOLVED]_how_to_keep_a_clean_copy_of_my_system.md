---
title: "[SOLVED] how to keep a clean copy of my system"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-23
what folders should i copy to redo my system easy?
i already have an aptoncd disk made.
then how do i copy the folders back to a new install?
like the home folder or etc folder ??

thanks everybody,
DarinB

---

### Post by scrooge_74 on 2007-08-23
definitely keep your /home folder and copy /etc

---

### Post by DarinB on 2007-08-25
i thought i read of three or four folders to save??
which are they??
how do i put them back?? 
i finally go the home folder copied and the hidden files t an external drive formatted with ext3.
what else should i add???

so far i have remember home with hidden and etc ,,,does etc have hidden files as well????
thanks db

---

### Post by scrooge_74 on 2007-08-25
Check this[ link]("http://www.psychocats.net/ubuntu/separatehome") is good for making separate /home partitions

---

### Post by david_e on 2007-08-25
> **DarinB said:**
> so far i have remember home with hidden and etc ,,,does etc have hidden files as well????
thanks db
I think that /etc has no hidden files. 

I think that the best way to keep a clean copy of the whole system is to backup the full root filesystem "/". It is not that big to backup everithing (the only big directory usually is /home where one keeps his mp3s videos etc...). Maybe you can make a separate /home partition.

A compressed tarball of the whole root (excluding /home) should be about 5-6 Gb... not that much. Keeping only /etc is not a big deal since there are very few files in there that where not generated automagically for you. I think that it would be faster to just reinstall everything on an empty root...

All your stuff and most of your customizations are in the /home directory...

---

