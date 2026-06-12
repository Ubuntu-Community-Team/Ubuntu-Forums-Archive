---
title: "Getting Amount of Disk Space on and HD"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by funklick on 2005-06-27
Hi,

This is super basic, but I haven't been able to google an answer to this question:
How does one find out how mush space it left on a partition or hard drive from the command line?  I thought 'free' might be my answer, but that's for RAM and VM.

thanks,
wes

---

### Post by Xian on 2005-06-27
If you know the partition you can express it in the command.
Otherwise, just use the generic 'df' command and it will list all mounted partitions.
```
$ df /dev/hda1
```
```
$ df
```

---

### Post by skoal on 2005-06-27
try typing in a terminal 'df'. You'll see the percentages.

/edit Oops! I guess I need to be quicker...

\\//_

---

### Post by dmsynck on 2005-06-27
You should be able to get the info you are looking for with the following:

df -h /dev/hda?

Breakdown as follows:

df (disk free /bin/df)
-h (make it easier to read)
/dev/drive and partition # e.g. /dev/hda2

Hope this helps.

---

### Post by funklick on 2005-06-27
Muchas Gracias !

wes

---

