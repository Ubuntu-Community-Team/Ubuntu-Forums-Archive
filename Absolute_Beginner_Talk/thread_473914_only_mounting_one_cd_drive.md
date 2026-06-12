---
title: "only mounting one cd drive"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-06-14
running feisty finds cd burner but not the dvd drive

---

### Post by Damanther on 2007-06-17
Can you post the contents of your /etc/fstab file pls?

---

### Post by weel on 2007-06-17
/etc/fstab would definitely be useful information. The other thing we'd likely need to know is the output from these commands:

```
ls /dev/sd*
ls /dev/hd*
```

Those commands will tell you what SCSI and IDE device the kernel thinks it can talk to at the moment. (I'm not entirely sure what determines whether certain newer kinds of devices end up being classified as sd* or as hd*; on my machine it seems to depend on certain kernel boot options; that's why I'm asking you to run both commands.)

---

### Post by JParkus on 2007-06-18
parkus@parkus-desktop:~$ /ect/fstab
bash: /ect/fstab: No such file or directory
parkus@parkus-desktop:~$ parkus/ect/fstab
bash: parkus/ect/fstab: No such file or directory
parkus@parkus-desktop:~$ ls /dev/sd*
ls: /dev/sd*: No such file or directory
parkus@parkus-desktop:~$ ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5  /dev/hdc
parkus@parkus-desktop:~$

---

### Post by Damanther on 2007-06-20
For the fstab file type:

sudo cat /etc/fstab

It looks like it only recognizes one CD according to the listing from /dev. 
/dev/hdc

---

### Post by JParkus on 2007-06-24
for everyone thats been helping me with the one cd drive issue i found the problem. 

I AM AN IDIOT  

So one of the many times I was play around inside the puter  I somehow pulled the Cable out
thanks anyway. At least I learned something new .

---

