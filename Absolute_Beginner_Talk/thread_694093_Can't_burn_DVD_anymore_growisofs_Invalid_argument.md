---
title: "Can't burn DVD anymore: growisofs: Invalid argument"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by hanexar on 2008-02-11
Hi, 
I'm not burning DVD very often, but it used to work perfectly. But today I tried to make a backup with k3b, and I got this error coming from growisofs

```

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/scd1: flushing cache
/dev/scd1: updating RMA
/dev/scd1: closing session

```

I tried the same operation directly with growisofs in a terminal and I received the exact same error. It's pretty annoying because it scrap a DVD each time. 

I can't say what change broke this, because, as I said before, I'm not using my burner very ofter (last use goes back for 3-6 months).

---

### Post by dstew on 2008-02-11
> builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0The device name for the input file seems strange. Shouldn't it be```
builtin_dd if=/dev/fd0 of=/dev/scd1 obs=32k seek=0
```? I might not understand this device. But I never saw a linux device with a name like that.

---

### Post by hanexar on 2008-02-11
Yea, it seems weird, but anyway, when I started growisofs with command line, I used /dev/dvdrw, which is pointing to the good drive according to my dev list, and I still got the same error. Anyway, the burner is scrapping my Dvd, so I guess it's not a problem to find my device...

Thanx for your help!

---

