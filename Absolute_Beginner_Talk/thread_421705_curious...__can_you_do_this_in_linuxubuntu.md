---
title: "curious...  can you do this in linux/ubuntu?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-24
ok.  windoze has this thing called defragging.  it doesn't really matter, but i can't get it out of my head.  can you do this in linux/ubuntu?  or is it just a cheap way of covering up some flaw in windoze that doesn't exist in ubuntu?

---

### Post by jfinkels on 2007-04-24
> **locke.dragon said:**
> ok.  windoze has this thing called defragging.  it doesn't really matter, but i can't get it out of my head.  can you do this in linux/ubuntu?  or is it just a cheap way of covering up some flaw in windoze that doesn't exist in ubuntu?

Defragmenting your hard drive moves 'chunks' of files around so that all the 'chunks' of one file are physically next to each other on your hard disk drive.

We don't need to do it, because our operating system writes to the filesystem in a different way, essentially using space more efficiently. Also I think it does some small defragmenting here and there without you even noticing.

---

### Post by LaRoza on 2007-04-24
You do not need to.

---

### Post by kevinlyfellow on 2007-04-24
Windows is terrible with file management.  I've heard that there is a way to defrag ext3, but don't bother because its not too fragmented.  Next time you boot and it checks your filesystem, note how much is "non-contiguous" or in other words fragmented.

---

### Post by Fenrirwulf on 2007-04-24
Apparently it can be done though if you really want to do it.

[http://packages.ubuntulinux.org/warty/admin/defrag](http://packages.ubuntulinux.org/warty/admin/defrag)

---

### Post by locke.dragon on 2007-04-24
ok.  cool!  i knew ubuntu was better!  but is there any way to make it run faster?  i know it's lightning fast already, but when you defrag windoze, it makes it run faster.  any ideas?  i'm still just curious.  it's not the end of the world if it can't be faster.

---

### Post by LaRoza on 2007-04-24
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by jfinkels on 2007-04-24
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting) This article explains it!

EDIT: Darn you LaRoza! I had to find it!

---

### Post by johnc4510 on 2007-04-24
A graphics card will always help you system run faster. And it doesn't have to be a top of the line card. I use a nvidia FX 5500 which I got on sale for around $59. If you don't have a graphics card that is. I would recommend nvidia or ati though.

---

### Post by kinematic on 2007-04-24
After runnig GNU/Linux for 2 years my data partition has 0.8% non-contiguous files,my home partition 1.2% and my root partition 0.7% non-contiguous files.
this just goes to show how efficient the ext3 file systemis.

---

### Post by kevinlyfellow on 2007-04-24
Check this out
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

Edit: Be careful with some of their suggestions.  Its a nice place for ideas though

---

