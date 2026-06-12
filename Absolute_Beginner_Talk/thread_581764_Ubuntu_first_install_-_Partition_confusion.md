---
title: "Ubuntu first install - Partition confusion"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by prob69 on 2007-10-19
Hi, I am very new to this but determined to give it a shot but really confused about the partitioning side of it when loading the install from the Live CD. I have a 120Gb drive as to which I have partitioned. The first partition (c:) 52.2Gb which contains Windows Vista, the second partition (d:) 20.68Gb and the third partition is (e:) 38.89Gb. I have no data on D and E drives and I would like to install Ubuntu on Drive D therefore leaving drive E free.
When I install and it gets to the partitioning bit, if I select the first option it says that it will resize the D drive and I am reluctant to do this as the first time it created partitions all over the place and not the size partitions that i wanted. I can't make sense of the slider bar as it always seems to default halfway along the slider. What happens if I increase or decrease the slider? Is there any simple documentation anywhere?
If I select Manual install I select the 2nd partition thinking that Ubunto will be installed on that partition and it says I need to create a root partition. I wish I had a complete spare drive to install this on as It would seem that its alot easier, but I hav'nt.
Basically the upshot is, all I want to do is install Ubuntu on the second partition and thats it. Please help it is driving me nuts. It is probably so simple but i can't acheive it.
I think i need and idiots guide to installing ubunto!

thanks guys n gals

---

### Post by Pumalite on 2007-10-19
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by prob69 on 2007-10-19
That looks like just the job. I will have a try and see what happens. Thanks for the quick response, much appreciated.

---

### Post by skotadi on 2007-10-19
I haven't actually installed gutsy yet, so this may be a little different, but here goes.  

1. select manual partitioning.

2. select the partition you want to install ubuntu on, and resize it to be smaller than the original (you'll need 3 partitions total, so make room for all of them inside the space where your original 1 partition was)

3. make that the root partition (that merely means the "root" of the filesystem.  It should show some kind of filepath to the partition in a dropdown menu.  select or type in "/" (i think without the quotes though).  
Make the filesystem for this partition ext3.

4. Now make a new partition in the unpartitioned space - about 1 gig will be enough.  Select "page" or "swap" for the filesystem (I forget which one it's called). This partition is just for your swap/page (equivalent to the windows "page file")

5. Now, make a final partition in the unpartitioned space (or, use your "E" drive or some other partition or whatever your want).  This is going to be your "home" partition.  This will store your "home" folder, containing all your documents and programs (similar to the "documents and settings" in Windows).  Set the filepath to the "home" option in the dropdown.  Set the filesystem to ext3.

Obviously, make sure you're repartitioning the right drive or you'll reformat right over your data.  (sounds obvious but I've very nearly made that mistake.)

Hope that helps

Edit: Doh!  didn't reply fast enough!

---

### Post by William S on 2007-10-19
Gparted live CD can also be used. But it is very important to be careful, that you don't do something you don't really have control over otherwise things can be screwed.

---

### Post by prob69 on 2007-10-19
Thanks guys. The D partition that i want Ubunto to be installed on is currently NTFS. Do i have to make this blank or format in another format before i run the install and start the partitioning?

---

### Post by Pumalite on 2007-10-19
The installer does the formatting anyway. Point to the right partition.

---

### Post by prob69 on 2007-10-19
Thanks again. Being all new to this, I am very impressed with the quick responses. Keep up the good work!

---

