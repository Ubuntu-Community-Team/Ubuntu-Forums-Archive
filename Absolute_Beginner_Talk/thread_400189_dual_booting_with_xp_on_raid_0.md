---
title: "dual booting with xp on raid 0"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by dunkemdeep on 2007-04-03
Hello everyone
I'm mainly a pc gamer who wishes to use my pc for for more than just games. i have been using gimp for some time now and going from people at gimptalk they use linux for a lot more, so i thought i would be up for something new.
here is my system specs
amd64 dual 3800
asus a8n sli delux
2gb memory
2 x 34gb raptors in raid 0
200gb ide drive
xfx7600xxx
 i use sehniser usb headset and mic for sound so no need for sound cards

i have downloaded ubuntu 6.10 64bit and have made the boot disc.

here is my problem. I have just done a format of my pc and after setting my raid 0 up again i created a partition on the drives with xp being on one of these partitions, but the second partition i allocated a drive name e.g F instead of leaving unallocated. the second partition was also formated with the ntfs format.
I then inserted the ubuntu boot disc and restarted my pc so that i could install it to the second partition. however ubuntu sees the raid as two separate drives and wants me to create a partition.
how do i install ubuntu to the partition i have already created.

thank you in advance for any help given, I'm sure it will be the first of many:)

---

### Post by dunkemdeep on 2007-04-03
i have looked about and i don't seem to be able to find a post with the same problem. is there anyone who may be able to help:)

---

### Post by Zuph on 2007-04-03
I can't solve your problem, but I can tell you that running RAID 0 is an absolutely horrible idea.

If you lose one drive, you lose all the data on both.  Don't ever store anything valuable on a RAID 0 setup unless you like losing valuable things.

---

### Post by dunkemdeep on 2007-04-03
i use raid 0 for gaming m8 online and use my 200gb hard drive for all my data:)

---

### Post by dunkemdeep on 2007-04-04
its ok i have sorted it.
i formated again, set up the raid 0 and put a partition on but left the second partition unallocated. after installing xp to the main partition i then installed ubuntu which seen the unallocated space and let me install.

I know I'm new to both linux and these forums, I am not however new to forums in general. Although the staff here do a good job and members are nice, polite and helpfull were posible I have too say that the biginner section is a bit overwhelming and many posts are not replied too because of the number of people posting for help. Would it not be better to brake the biginner section down into other sections were people can post for help in the relivent areas and therefor stop a persons posts for help disapearing to page 10 within a couple of hours without the posability of getting a reply:)

---

