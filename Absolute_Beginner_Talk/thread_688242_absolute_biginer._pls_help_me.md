---
title: "absolute biginer. pls help me"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by imashwani on 2008-02-05
[COLOR="Red"]how can i make the partitions in ubuntu 6.06 lts , what should be the ratio of partition if i have 40 gb hard disk ?

after instalation what should i do next ?[/COLOR]

---

### Post by jken146 on 2008-02-05
If you're a complete beginner I'd recommend installing 7.10 (Gutsy Gibbon) rather than 6.06.  I think it's too outdated for most new users (although if you have a reason to use Dapper then please go right ahead!).

I can't remember how the installer works for Dapper, but if Ubuntu is the only OS on your hard drive, you will be alright using the default options.

After installing, it's ready to use!  Explore Ubuntu a bit, and maybe read some documentation. [https://help.ubuntu.com/](https://help.ubuntu.com/)

Don't hesitate to post here if you have more questions!
Welcome to Ubuntu!

---

### Post by drs305 on 2008-02-05
This is one of the best unofficial sites that can answer lots of your questions:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

We're here to help if you need it. Welcome to ubuntu!

Added:
Here is a previous post with lots of useful links for newbies:
[http://ubuntuforums.org/showthread.php?t=648383#2](http://ubuntuforums.org/showthread.php?t=648383#2)

---

### Post by kpkeerthi on 2008-02-05
Just start the ubuntu installer and you will be presented with partitioning options. You'll be presented with options to use whole disk (if that is what you are upto). Also, check out the links in my signature. 

And btw... You can order ubuntu CDs from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/). I received gutsy in about 3 weeks.

---

### Post by jan quark on 2008-02-05
welcome to ubuntu


some thoughts

psychocats site is great :)

ubuntu needs a /      partition, thats the name of it don't ask :)
and               a swap partition, something like additional memory
you can add   a /home partition to store your personal data in an extra partition if something goes awry

ubuntu uses ext3 as the file formal so you need to format the driver first, but this happens automatically during the installation

read a bit about partitioning and everything will be fine

feel free to ask

---

### Post by Keks01 on 2008-02-05
if you want to make/edit partitions, you should install a partitioner.
in terminal:

```
 sudo apt-get install gparted 
```

that should give you a fairly simple GUI tool to make and modify partitions.
run it with

```
 gksudo gparted 
```

WARNING! you can wipe out an entire hard disk using this if you're not careful and do not know what you're doing =)

---

