---
title: "Mounting hdb1 on startup"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Michiba on 2006-05-16
Hello all,

I have a slave drive installed that holds backup (virus proof) info from my windows network. I mount the drive (hdb1)  under the root as /storage. Due to ignorance I do this manually after start up. What lines do I add to fstab to do this automagically on boot up ?

Thanks in advance

Michiba

---

### Post by iball on 2006-05-16
What filesystem is it?  I will assume ext3, but substitute whatever file system you are using in the line below.  You can find the supported filesystems in "man fstab"

Basically you need a line in /etc/fstab that looks something like:
```
/dev/hdb1       /storage      ext3    defaults        0       2
```

I hope this helps
--Ian

---

### Post by Michiba on 2006-05-16
Thanks Iball,

I use ext3 and works like a charm.

Cheers
Michiba

---

### Post by Michiba on 2006-05-16
The line makes sense but what is 

default 0 2 

telling my system????

Michiba

---

### Post by iball on 2006-05-16
default is just saying to mount the device with the default attributes.  I am not 100% sure what they are, but they would be something like: rw (read-write), auto (mount on boot), ...

See "man mount" for more mounting options.

The 1st number is to do with dumping the file system (don't know what that is) and the 2nd is to do with the order fsck checks on bootup.

I hope this helps
--Ian

---

