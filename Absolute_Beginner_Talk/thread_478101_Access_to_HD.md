---
title: "Access to HD"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by l1oyd on 2007-06-19
I know this must be a common question but I'll ask anyway.

I have two drives.

Master with 20GB/60GB Both NTFS
Slave with 20GB Ext3

I have XP on the Master 20GB
and Ubuntu on the Slave.

Now I'm pretty sure I read somewhere that I shouldn't have put Ubuntu on the salve but that point aside.

Why can I not access the 60GB without SUDO? I can understand it if I couldn't access the windows install, but my free 60GB is locked?

Not a huge issue (i am getting faster at using console commands) but it would be better if I didn't have to do it from root.

Cheers

---

### Post by joe.turion64x2 on 2007-06-19
You need to change the permissions to access your 60GB drive, I mean, change the permisions of the folder where it is mounted.

Joe.

---

### Post by l1oyd on 2007-06-19
Sorry for dragging it out but where or how do I change the permissions in console.

I kind of got sent to look at /etc/fstab from thread [Can not change permissions]("http://ubuntuforums.org/showthread.php?t=217492")

But the drive I want to change permissions to is not there.

Cheers

---

### Post by joe.turion64x2 on 2007-06-19
The command to change permissions is **chown**, you may need to run it as root (sudo chown). Type **man chwon** to learn all its options.

Joe.

---

### Post by l1oyd on 2007-06-19
I seem to get the same error as using chmod

> chown: changing ownership of `/media/Data/': Read-only file system

what am I missing?

---

### Post by joe.turion64x2 on 2007-06-19
> **l1oyd said:**
> I seem to get the same error as using chmod



what am I missing?
MMM, I forgot to mention that Ubuntu does not allow full read/write capabilities to NTFS volumes by default...you might need to install ntfs-3g or something similar.
Anyway you should be able to change permissions for the mount point (the folder where you mount the drive) only. 
Joe.

---

### Post by maddot on 2007-06-19
> **l1oyd said:**
> Now I'm pretty sure I read somewhere that I shouldn't have put Ubuntu on the salve but that point aside.


Where did you hear that from? I have my ubuntu in slave and it's behaving just fine :) I feed it oreos. hmm... 

> **l1oyd said:**
> 
MMM, I forgot to mention that Ubuntu does not allow full read/write capabilities to NTFS volumes by default...you might need to install ntfs-3g or something similar.


it doesn't read and write? But my system read and wrote on my windows ntfs partition just fine with a clean install....am i missing something here O.o

---

### Post by joe.turion64x2 on 2007-06-19
Ok, if your system already reads/writes ntfs you are a step ahead.

---

### Post by l1oyd on 2007-06-20
ok, I have now installed ntfs-3g but still only have Read Access that particular drive...

Anyone have an idea?

---

### Post by l1oyd on 2007-06-20
bump

---

### Post by l1oyd on 2007-06-20
Thanks guys,

After a bit of playing around with mounting and unmounting drives, throw in a reboot or two and presto. I can now write to both my NTFS partitions, thank you to everyone's help.

---

### Post by joe.turion64x2 on 2007-06-20
It is good to know you got it sorted.

---

