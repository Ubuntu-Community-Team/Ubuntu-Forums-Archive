---
title: "300 gig partition now free space...undo?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2008-03-05
So i was fooling around with ubuntu's partitioner and I ended up making my 300 gig ntfs partition become freespace, when in reality I have a whole bunch of pictures,videos ect located in that partition. How do I restore that partition and not lose what is on that partition.

---

### Post by Baelari on 2008-03-05
i think you're screwed ;;

---

### Post by endlessurf on 2008-03-05
lol, i hope not, I am looking for a way around now.  You have any ideas?

---

### Post by Baelari on 2008-03-05
as far as I know, when it's reformatted it's wiped clean. I don't know where a 300GB partition would even back itself up to. There's stuff investigators use to check crime scenes, maybe...

---

### Post by 3rdalbum on 2008-03-05
Did you apply the changes? If not, then just quit Gparted and it won't write any changes to disk.

If you did tell it to apply, then you need to restore your partition from a backup. Unfortunately, anything that you need to access through "sudo" or "gksudo" is unappropriate for playing around with, especially anything to do with partitioning!

If you don't mind paying through the nose for data recovery services, then immediately kill the power to your computer and remove the hard disk drive, then take it to a data recovery service. There are ways of recovering data, but you probably won't have 100% success.

---

### Post by endlessurf on 2008-03-05
I think i am going to use testdisk to get it back

---

### Post by endlessurf on 2008-03-05
woot woot got it back

---

