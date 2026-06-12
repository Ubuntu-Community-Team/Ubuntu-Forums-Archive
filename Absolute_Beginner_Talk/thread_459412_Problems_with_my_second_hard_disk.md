---
title: "Problems with my second hard disk"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by elpichi on 2007-05-30
alright my friend gave me his old 80gb hard drive on which he had ubuntu on, and i put it as a slave on my computer, the problem is that is readable only, and the file system is ext3, if it was ntfs i could at least write on it. 
how can i have permissions to write on that hard drive? or should i just format it to ntfs? =\

---

### Post by depele on 2007-05-30
may be you should try to mount it with the rw option?

or chmod the directory. to 777

```
sudo chmod 777 /dir/to/mount/folder 
```

It is just an option . There may be a better solution

---

### Post by elpichi on 2007-05-30
eek lol i didn't get that, a simple reformat with my windows cd did the job, thanks anyways ;)

i might have to do some research on chmod

---

