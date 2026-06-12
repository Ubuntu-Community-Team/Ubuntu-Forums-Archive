---
title: "Trying to find hard drive info"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by dross on 2005-08-03
I looked in the GNOME Device Manager to find out the size of the hard drive on my machine (I haven't used this box in a while, so I can't remember all it's specs).  Unfortunately, Device Manager is just giving me a bunch of "Unknown" values.  Is there another place I can look for this information?  THanks a lot!

---

### Post by Kyral on 2005-08-03
doing a df -h on the command line will print out the size, amount used, and mountpoint of all partitions mounted.

Just add up all the values for one device and there you go

---

