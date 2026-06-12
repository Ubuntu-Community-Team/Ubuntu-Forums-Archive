---
title: "I am so confused; need partitioning advice"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by sharar on 2007-03-08
I am trying to install ubuntu and I am at the partition page. I want to use 30 GB for ubuntu and am stuck. Please tell me what to do./=

---

### Post by gtratter on 2007-03-08
Please tell us more:
- what OS do you have currently installed
- how  big is your HD
...and then we will take it from there...

---

### Post by sharar on 2007-03-08
Windows XP
320 GB

---

### Post by sharar on 2007-03-08
[IMG]http://i90.photobucket.com/albums/k242/shararm/Screenshot.png[/IMG]

---

### Post by koshari on 2007-03-08
first thing you need to do is defrag your windows partition so it places all the data at the beginning of the partition, 

after that use gparted on the the live disk to resize the windows partition so you have room to create some linux partitions (20 gig will be heaps), 

then create a swap file at the end of the drive space of say 300 meg, and then create an ext3 partition between the windows and swap partitians.

---

### Post by sharar on 2007-03-08
Well um I can do the first one, but how do I do the other 2

---

### Post by koshari on 2007-03-08
are you still using those fat partitions?

---

### Post by koshari on 2007-03-08
to resize the ntfs partition just select it and in the options select resize, do this to release 20 gig, it would be a good idea to keep your fat32 partition as both windows and linux can wrtie to that partition,

---

### Post by koshari on 2007-03-08
another tip, the latest gparted is abailable on a live disk and is a bit better than the ubuntu version as the ubuntu versions are always a little dated.

---

### Post by old_geekster on 2007-03-08
Here is a guide that should help you:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It has pictures of each step of the process.

Also, there are videos on "Youtube" that may help you.

---

