---
title: "which dir do i install my tar.gz's to?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by rozilla on 2006-12-11
on my dapper, when i install .deb's it's just double-click and the rest is spectating, right? but what happens when i have tar.gz's and i have to extract them to someplace to run ./configure?
where would that someplace be? /usr? /usr/local?
please help.

---

### Post by taurus on 2006-12-11
You can unpack it anywhere you want, probably in your $HOME directory.  If you download it, it will be save in ~/Desktop so just unpack it from there...

```
cd ~/Desktop
tar xvzf **filename**.tar.gz
cd **filename**
./configure
and so on...
```
Once you have built and installed it, you can remove the source from your system.

---

### Post by marx2k on 2006-12-11
> **rozilla said:**
> on my dapper, when i install .deb's it's just double-click and the rest is spectating, right? but what happens when i have tar.gz's and i have to extract them to someplace to run ./configure?
where would that someplace be? /usr? /usr/local?
please help.

On my system I just extract them to ~/install/<program name> and go from there

You can always make /usr/install 

Or really anywhere you would like to keep your collection of source files.

---

### Post by rozilla on 2006-12-11
thanks guys!!

---

