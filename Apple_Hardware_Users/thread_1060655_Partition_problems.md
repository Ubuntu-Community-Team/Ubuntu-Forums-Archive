---
title: "Partition problems"
date: 2009-02-05
forum: Apple Hardware Users
---

### Post by gunfart on 2009-02-05
Can anyone give me some advice on this?  I installed OSX 10.2 and now want to just host Ubuntu but it keeps locking up on me.   What step in the installer to I have to take to go forward with this install?Partition hangs up on "#3 of Ide1 master (hda)"

---

### Post by tiresia on 2009-02-05
Please, give us more info about your computer and the ubuntu you are trying to install

---

### Post by gunfart on 2009-02-05
it's an imac dv g3 600mz  40 gigs hard drivewith a gig of ram.  I am trying to install ubuntu 8.10 from the alternate powerpc iso.  I am trying to overwrite the hard drive so it only has the linux system. currently it has osx 10.2

Thanks!

---

### Post by tiresia on 2009-02-05
What do you mean, you are trying to overwrite? 
During the installation, when the partitioner asks you how you want to install Ubuntu, just choose the whole hd. Are you doing this?

---

### Post by gunfart on 2009-02-05
I am choosing a Guided install on the whole disk.

I have 4 options:

1. Guided - use entire disk
2. Guided - use entire disk and set up LVM
3.  Guided - use entire disk and set up encrypted LVM
4. Manual

What's LVM?

I chose to:3.  Guided - use entire disk and set up encrypted LVM

and I get the message "The ext3 file system creation in partition 3 of IDE1 master (HDA) failed.

I hit continue and then it just hangs up on me.

Any ideas? Please?

---

### Post by tiresia on 2009-02-06
LVM = [http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

Choose the first option to install. 
After installation you will most probably need to edit the file /etc/X11/xorg.conf (as everyone on an imac g3). Please, read other similar thread on this issue.
Let us know.

---

### Post by gunfart on 2009-02-06
Thanks Man!  It is installing the base system now.....yeah!:popcorn:

---

