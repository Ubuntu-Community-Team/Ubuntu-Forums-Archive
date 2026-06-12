---
title: "what is the default partiton in ubuntu"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by black1 on 2007-02-26
i have asked this before somewhere and never recieved any replies.

whan you install Ubuntu and write over the whole hard drive and use the default install and do not partiton on your own....what is the actual partition?  is there a 2 GB swap file? what other partitions are there?  I am trying to dins out - I know zero  about partitioning but I did want a 2GB swap partiton. and I wasn't sure when I install over the complete HD and deafult install what I actually end up having?

please - serious knowledgeable answers and not guesses or assumptions.

thank you.

---

### Post by mikewhatever on 2007-02-26
You should get at least two partitions, root and swap. Swap doesn't have to be 2 GB, it depends on the size of RAM. Look here for more picturesque explanations [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

May I ask the reason for 2 GB of swap?

---

### Post by black1 on 2007-02-26
thanks for the link.

2 Gb because i want a larger swap partition. I was told and i agree that you should have double your ram. and I have 1 GB was not going to spend the extra for the 2GB now. so I want a large swap file - i also heard it runs a heck of a lot better with a larger swap due to linux mostly on memory/ram and swap.

thanks.

that is the best answer I can give you at the moment.

---

### Post by igknighted on 2007-02-26
Ubuntu defaults to 2 partitions (swap and /).  Many distro's default to 3 partitions (/, /home, and swap).  Sabayon Linux and several others use /boot as the first partition and then / and swap in an LVG (logical volume group).  To know if you have used the whole hard drive, try running the command 'sudo fdisk -l' and it will tell you what partitions and empty space you have on your drive.

As for the swap size, I have 1gb ram and never use more than 1gb swap.  Swap is only used when the ram is ful, and 1gb ram will almost never be full.  If I ever touch my swap it is a rare day indeed.  That said, if you have a lot of HD space then it never hurts to have more.

EDIT: Ubuntu will say all the ram is in use most of the time, because it is being used for caching.  If an app needs the ram, the caching moves to the HD.  Unused ram is wasted ram, thats the linux philosophy.

---

### Post by mikewhatever on 2007-02-26
Unlike Windows, Ubuntu seems to be more economical in the use of resources. I think, unless you are going to do alot of video editing, 2 GB of swap would be a waste. It is not a big deal really, but I also have 1 BG of RAM and 900 MB of swap, and swap is never in use, while Ubuntu uses about 600 MB of RAM.
> free
             total       used       free     shared    buffers     cached
Mem:       1034152     356252     677900          0      11276     190208
-/+ buffers/cache:       154768     879384
Swap:       947792          0           947792


---

### Post by Rui Pais on 2007-02-26
> **black1 said:**
> thanks for the link.

2 Gb because i want a larger swap partition. I was told and i agree that you should have double your ram. and I have 1 GB was not going to spend the extra for the 2GB now. so I want a large swap file - i also heard it runs a heck of a lot better with a larger swap due to linux mostly on memory/ram and swap.

thanks.

that is the best answer I can give you at the moment.

hi, that an old myth from the days when ram was expensive. 
If you have 64Mb of ram make your swap at least twice... If you have 1 G it's already twice ;)
In fact, with 1G you hardly will use the swap at all... linux manages the ram very well... you will only waste space.

The question about default partition is weird... 
It looks you are thinking as as Windows user.
Linux mounts default partition as / not matter the partition scheme. 
If you want to know name and position of your partitions, try on a terminal:
```
gksudo gparted
```

---

### Post by Songwind on 2007-02-26
Also, the partition software that comes with Ubuntu works very well for resizing partitions, so if you ever find yourself needing 2Gb of swap you can always shrink your / partition by 1Gb and put it on your swap partition.

But even under heavy load and multiple app use I have never used more than 20Mb of swap so far on my 1Gb machine.

---

