---
title: "2 HOMES - Partition permisssions question"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by stoer on 2008-03-10
Hi all,
Hopefully 2 easy questions to answer for somebody.
1.
I recently reinstalled 7.10 on a dual boot laptop;
Windows partition / Data partition /  Linux Partition

I had from my previous install my /home on the data partition  ( EXT3 ).

During the reinstall for one or another reason (unknown) i now have a /home on my linux (system) partition aswell.
Obviously i'd like to get rid of the new /home.  But transfer the contents to the old /home.  I'm still not entirely sure how to do this despite reading a couple of posts on this topic, i' don't want to muck my system up any more than it now is....

2.
My data partition is write protected, that is i can only make changes as ROOT and not as USER.
I am the only user and use this partition as storage for both Linux and Windows, My /home is also there!
How do i change permissions for a partition? I obviously need to be able to read/write/change/ and delete files.

Any help would be greatly appreciated.

---

### Post by jan quark on 2008-03-10
> How do i change permissions for a partition? 
```
sudo chown -R usr:usr CU
sudo chmod -R 755 CU
```

replace usr:usr with your username for instance john:john

replace CU with the path to your partition for instance /dev/sda1

---

### Post by stoer on 2008-03-10
That was quick !  :)

Many thanks for that, really appreciate the help.
Works as well    ;)
Thanks.



Found a lot on moving /home, but most of it reads like this

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

which is fine, but i already have a partition set up /media/sda2  anyone know if i have to rename the partition first (to home ?), I thought i'd just move /home to this already existing partition - or am i just getting myself confused ?
I'll go and read further before trying the above link, much further...

---

