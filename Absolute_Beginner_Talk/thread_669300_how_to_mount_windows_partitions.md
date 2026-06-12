---
title: "how to mount windows partitions"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-16
please tell me 
i have installed ubntu on my hard drive
now as  I am going through
I am looking for the drive d on which i have my songs my pdf's and movies and all stuff which i need daily
but i cant find it
is it that i have not mounted it
or is it i am not able to locate it
please tell me how should i solve this

---

### Post by renzokuken on 2008-01-16
it's probably not mounted.

to automount it with full read/write capabilities simply open a terminal and run

```
sudo apt-get install ntfs-config
```

this will install some software that automounts any ntfs drives with full read write (i'm assuming your "d" drive is an old windows drive formatted in ntfs, if not you'll have to do it another way.)

---

### Post by erginemr on 2008-01-16
If the above trick does not solve your problem, please post the output of these two commands on the console:

```
cat /etc/fstab
```

```
sudo fdisk -l
```

---

### Post by stchman on 2008-01-16
> **coolnik6 said:**
> please tell me 
i have installed ubntu on my hard drive
now as  I am going through
I am looking for the drive d on which i have my songs my pdf's and movies and all stuff which i need daily
but i cant find it
is it that i have not mounted it
or is it i am not able to locate it
please tell me how should i solve this

I have a tutorial on partition mounting in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

the ntfs-config package is also really easy.

---

