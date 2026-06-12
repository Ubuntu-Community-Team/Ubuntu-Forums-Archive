---
title: "How to partition my harddrive"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by linuxismywife on 2006-11-14
[IMG]http://img132.imageshack.us/img132/9895/diskic5.png[/IMG]

How do you partition off the free spaces in between the partitions???

I have 100gb free spaces stuck within!!

---

### Post by justplayin on 2006-11-15
I'd boot a LiveCD and extend the neighbouring partitions onto the free space. But first write down the "names" and sizes of all your partitions, backup your important data, defrag your windows partitions. Take a LiveCD like [knoppix]("http://www.knopper.net/knoppix/"), i found that the included qtparted worked better than the gparted you find in Ubuntu.
When your in qtparted you can "slide" the sides of the partitions you want to make bigger onto the free space of your harddrive. But beware, because after merging the partitions like this, they might change their names. hdb5 might become hdb7 etc. So you will have to identify them by doing a
```
sudo fdisk -l
```
or under knoppix it's
```
su fdisk -l
``` i think.

Just make sure you check and recheck everything your doing here twice, and backup everything that's important. Maybe you will have to change the names of the partitions in your /etc/fstab to get the pc to boot and mount your partitions correctly, because, as said before, their names may change.

And make sure you don't reformat your partitions with data on them!

The best thing would be to print out some guides about using gparted or qtparted. Take a look at [this]("http://www.psychocats.net/ubuntu/installing"), [here]("http://www.extremetech.com/article2/0,1697,1928205,00.asp"), [here.]("http://wiki.linuxquestions.org/wiki/Partition")

Btw, how did you get that much free space in between your partitions?

---

