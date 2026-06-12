---
title: "Sharing data with another linux distro"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-26
Hi there.

I'm currently using Dapper (and happy with it); I wiped off widows xp. Just I was wondering, what in case if it comes to my mind to install another linux distro together with dapper, would it be possible to share data between the two?
If the possibility isn't run out, would that be byu default, or do I have to install something?:-k 

Thanks for patiently reading and for any suggestion

---

### Post by insane_alien on 2006-12-26
entirely possible. you'll be able to mount the ubuntu partitions in the other distro and the other distros partitions in ubuntu. they will be entirely accessable

---

### Post by neowolf on 2006-12-26
Entirely possible, any Linux distribution can read the **ext3** filesystem that Ubuntu uses, unlike  Windows's **NTFS** which can only be fully read and written to by Windows itself.

```

su;
mkdir /mnt/ubuntu
mount /dev/hd{number of ubuntu partition} /mnt/ubuntu

```

---

### Post by helphope on 2006-12-26
Thanks for replying.
Now I'll look for mount and what it does.

---

### Post by Sef on 2006-12-26
Read Psychocat's [Mounting Linux]("http://www.psychocats.net/ubuntu/mountlinux") tutorial.

---

### Post by helphope on 2006-12-26
Thanks for the speedy reply.
I had a look at the link you suggested, but just I don't understand the utility of this command.
Every time I plug in a pen drive I can read it; likewise I can read everything in my hard disk.
Maybe if I install a new hard disk I should run the mount command? :confused: 
I can't understand the utility in case of a new distro.

---

