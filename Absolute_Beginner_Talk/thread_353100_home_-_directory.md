---
title: "home - directory"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by niki001 on 2007-02-04
Hi all,

I've got a bit of a problem I haven't been able to solve yet. So I'm hoping somebody could help me out. I installed Kubuntu 6.10 on a Dell8300 and everything up and running without any major problems. I've got my home directory on the default place (given by Kubuntu on install).
I've made a new Linux Ext3 partition as hda4 and I would like to use it as my home-directory.
Can anybody tell me how I can make Kubuntu use this HD as my home-directory. That way I hope I can use this directory again (with all settings I made in the past) when I have to reinstall my Kubuntu after I messed it up :lolflag: once again.

thx
greetings
niki

---

### Post by housam on 2007-02-04
Look at this guide , it may help:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by lamego on 2007-02-04
You just need to edit /etc/fstab, and change the /home entry to use your new partition.

---

### Post by niki001 on 2007-02-04
Thanks a bunch housam, this worked like a charm!!

---

