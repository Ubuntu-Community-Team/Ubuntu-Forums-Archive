---
title: "[SOLVED] Partition Dual Boot"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-18
hey quick question, i'm a little puzzled.  If you rerfer to the attached photo you will be able to see my partitions, i shrunk my vista partition big time using vista's built in partitioner, now when i boot the live CD and use GParted i ahve no idea how to move that free space to after my /home so i can extend my /home using all that free space.  Any thoughts???

Thanks, Alain

---

### Post by Drate on 2007-07-18
I *believe* you would right click on sda4 and select resize partition, then max it out.

---

### Post by S15_88 on 2007-07-18
tried that, since it has several extensions it won't unmount then when i unmount my /home can't expand it cause the free space isn't directly infront/behind.  this just has me puzzled!

---

### Post by AlexenderReez on 2007-07-18
> **S15_88 said:**
> tried that, since it has several extensions it won't unmount then when i unmount my /home can't expand it cause the free space isn't directly infront/behind.  this just has me puzzled!

one of the rules for partition is you can't create too many partition from one available space (just what you trying to do) unless you delete that partition and make new one...it is same if you have default partitioning by windows mbr like partition c,d,e and f...then you format f divide by 2...if you delete one of that partition,you can combine anymore...because it is more than limit...

---

### Post by meierfra on 2007-07-18
I would try the following:

unmount all the partitions.

increase sda 4 (maybe you can skip this step)

increase sda 5

decrease sda5 leaving the free space at the end

increase sda6

---

### Post by S15_88 on 2007-07-18
just to make sure i understood that correctly, you're saying i can't expand my /home anymore?

---

### Post by meierfra on 2007-07-18
Just to double check. I was assuming that sda6 is your home partition. Or is it sda5?

---

### Post by S15_88 on 2007-07-19
sda 5 the 32 GB, i want to expand that to 80 w/e using all that free space from vista, adn then i'm thinkng of fully wiping off vista and creating a VPC for it just in case i need to run something, i've got 2GB of ram so running it virtually won't be that bad.  my only concern about the partitioning is that /home, /root, and swap are extensions of one logical partition so i do i put that free space inside there?

---

### Post by S15_88 on 2007-07-19
?

---

### Post by meierfra on 2007-07-19
It seems that the gparted on the ubuntu live cd is not powerful enough.  But the gparted live cd is more powerful. So if you download  and burn the gparted live cd,  you should be able  to do your partitioning as follows:

increase sda 4

increase sda 5

(If  you don't have the super grub cd  I recommend burning a combined super grub/ gp-parted cd. You can find it here:

[http://forjamari.linex.org/forum/forum.php?forum_id=298]("http://forjamari.linex.org/forum/forum.php?forum_id=298")
)

---

### Post by meierfra on 2007-07-19
Why do you want to erase your windows partition? As long as you have  plenty of disk space left, I  would keep it.  Windows runs o.k on a virtual disk, but not as well  as from the hard disk.

---

### Post by S15_88 on 2007-07-19
ya i figure if i load my notebook up with too many movies or music i'll throw it onto an external HD.  but i'd like to expand my /home.  when i get off work i'll try the  GParted CD.

thanks, Alain

---

### Post by S15_88 on 2007-07-20
yup GParted live CD worked like a charm, well it took 3 hours to expand it by 80GB but it was all good! thanks for the help!

---

