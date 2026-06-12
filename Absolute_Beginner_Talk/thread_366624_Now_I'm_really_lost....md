---
title: "Now I'm really lost..."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by butterball on 2007-02-21
so.... i was told to use FAT32 to make my hard drive accessible to both windows and ubuntu... and i plugged it into my windows xp computer (the system i *thought* i knew better... and guess what? it's not even an option. any ideas on how i could do it?

---

### Post by mikewhatever on 2007-02-21
Don't quite understand the problem, can you elaborate a bit. Does Windows not recognize the second FAT32 HDD, or is it Ubuntu. Is it an external drive? USB? Firewire?

---

### Post by butterball on 2007-02-21
I've got it set up on Windows XP at the moment. (would linux be easier?) It's an 80 GB seagate (if that even matters). It's the slave drive on my IDE cable. ummm.... 
Normally when I want to format something i just right click, format, choose the options i want and start it up. but with this drive it doesn't have FAT32 as an option. Do i need to partition it first? Do you need more info?

---

### Post by xpod on 2007-02-21
Are all your jumpers on the hd`s set to the correct positions for this new drive you`ve just plugged in...Master\slave??

---

### Post by Think first on 2007-02-21
Windows Xp does not let you format partitions larger than 32 GB (if I remember correctly) with FAT32 because of the waist of diskspace the very large clustersize in that case. Don't use very large FAT32 partitions anywhere...

---

### Post by butterball on 2007-02-21
yea. it's all good to go. i move the hard drive at a minimum probably twice a day. it goes between my two computers. my windows system on my other computer crashed so i decided to try out ubuntu. my problem now is that i have NTFS and linux won't let me access it. so i'm trying to format the drive so i can once again use it on both computers. and it's not giving me the option for FAT32

---

### Post by butterball on 2007-02-21
> **Think first said:**
> Windows Xp does not let you format partitions larger than 32 GB (if I remember correctly) with FAT32 because of the waist of diskspace the very large clustersize in that case. Don't use very large FAT32 partitions anywhere...

so what you're telling me is that i do need to partition the drive first... can i do that with the ubuntu install disc? i can't remember and i know i don't have my windows cd anymore

---

