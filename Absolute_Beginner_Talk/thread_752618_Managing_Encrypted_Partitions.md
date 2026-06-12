---
title: "Managing Encrypted Partitions"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-04-11
I like to try linux distros all the time and always leave a partition for such hobbies, but since I've 
encrypted my primary Ubuntu partition, it's been a chore and a half to manage other operating 
systems with the boot record. The new installations usually want to install grub overwriting my 
complex grub entry for the encrypted Ubuntu partition which causes problems.

For the record, I have a /boot partition setup.

My question is, what's an effective way of installing new distros but keeping my Ubuntu information 
around on the record? Should I just note the grub entry and include it on any future installation? I'd 
like to see if anyone else has been in this situation.

Thanks!

---

### Post by bodhi.zazen on 2008-04-11
You can not (easily) share a separate /boot partition. During the install, if a partition is mounted at /boot it is usually formatted and over written.

See this link :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by shanepardue on 2008-04-11
I guess the separate partition isn't important when I install a new distro, I've been multi-
booting for years, it's just this encrypted stuff kinda threw me for a loop because I couldn't 
just add my entry by hand.. I guess I'll just write in my entry on the new grub install. I'll 
have to notate the encrypted entry as it's a little more complex.

---

### Post by bodhi.zazen on 2008-04-11
Have you tried chainloading ? If you have some experience chainloading makes multibooting much easier.

---

### Post by shanepardue on 2008-04-11
I haven't tried chainloading..not sure what that is.

I have run into a problem though..when I installed an additional distro on a separate 
partition, my grub entry I saved doesn't work with the new Grub install. I believe it has 
something to do with the reference of /dev/mapper/sda8_crypt. Doesn't this have to be 
unlocked to get that bootable? 

Thanks for your help, I appreciate it!

---

