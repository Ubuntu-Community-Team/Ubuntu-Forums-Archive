---
title: "daul boot windows and fiesty"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2007-03-30
i have 4 partitions on my hard drive one for windows and back up and the other 2 are ready for linux one will be used for the swap(1gb) and the other will be for the ubuntu os (25gb). how would i go ahead to install ubuntu without disrupting my windows or back up partitions?

---

### Post by zvacet on 2007-03-30
It is a standard procedure for most of as in this forum.you don´t have to be afraid to try install something new.During install you will come to partitioning step.You can choose between bigge free space or manualy(there are other solutions but these are common).Whatever you decide you will see your windows partition and free space.Make your Ubuntu partition like this:
1. root = no more then 10 GB       mountpoint /
2. home = rest of free space exept    mountpoint /home
3.swap =1GB

Home is important because that´s the place wich save your settings,data...and you can do reinstall, freshinstall or whatever but with separate home your data are safe.
On this page you will find all you need for now.

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

