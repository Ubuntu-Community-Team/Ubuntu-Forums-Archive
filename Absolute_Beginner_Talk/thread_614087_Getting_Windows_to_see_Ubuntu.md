---
title: "Getting Windows to see Ubuntu"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by The-Russ on 2007-11-15
Hello all,

     I've been using Ubuntu for a few months now and, of course I enjoy it very much. I'm dual-booting with Ubuntu and Windows XP. I was able to mount my Windows drive in Ubuntu so that I can access my files from there. But, from what I've been told, the same can't be done to get Windows to see Ubuntu. Is this true or has anybody found a way of doing so? Thanks for your help.

---

### Post by Mithrilhall on 2007-11-15
This worked great for me when I was dual booting XP and Linux.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ntu on 2007-11-15
I note that that link is for ext2 whereas ubuntu normally installs to ext3.

---

### Post by kevinatkins on 2007-11-15
i think it should still work - ext3 is just ext2 with journalling extension...

---

### Post by Whiffle on 2007-11-15
ext3 works fine with that driver

---

### Post by The-Russ on 2007-11-15
Thank you everyone. I'll give it a try later on and post the results afterward.

---

### Post by Druke on 2007-11-15
what about reiserfs ??? I've been using that for my massive drive, would like to be able to access it from windows. found a few comercial apps but theres got to be something oss that works.

---

### Post by kevinatkins on 2007-11-16
I think you might be out of luck with reiserfs - the only tools I've seen for windows accessing linux partitions is for ext2 / ext3..

---

### Post by The-Russ on 2007-12-10
I finally got around to doing it and it works perfectly. Thanks guys.

---

