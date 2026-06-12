---
title: "Mac Pro and Ubuntu and 5 gig partition"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by kitki83 on 2007-04-24
This is my situation, I try to install ubuntu but it would not let me choose the partition I set for it.

I have three hard drives for my mac pro, 1. Mac Os X 2. Windows XP 3. General backup (Broken into two partitions, 290gig and 5 gig,

5 gig is meant for the Linux distro just to mess around with. But the problem when loading Ubutu I cannot get it to choose that exact partition but instead selects the whole hard drive, I cant find some previous post with this situation. Can anyone let some light to my situation?

Thank you

---

### Post by oskarloko on 2007-04-27
Yes:

select the option of  manual partition on disk.

Remove your 5Gb parition to a new one, to ext3 type and ' / ' mount point.

Try looking what swap is and howto handle it: partition or swap file.

---

