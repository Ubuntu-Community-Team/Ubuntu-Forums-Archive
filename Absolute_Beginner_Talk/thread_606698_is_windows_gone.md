---
title: "is windows gone?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by c-2-6 on 2007-11-08
I'm fairly new to Linux. I installed Ubuntu yesterday on my PII machine, it's working fine, but I wanted to boot up my windows xp again, and have not figured out how. Have I lost xp? I have the disk and can reinstall it. But how can I set up a dual boot option? Thanks for any advice.

---

### Post by plinydogg on 2007-11-08
When you were installing, you should have seen a few different install options (e.g., install on entire disk, etc.). Which did you choose? If you chose "install on entire disk" than you probably overwrote your Windows partition.

---

### Post by mummra1 on 2007-11-08
It depends on how your windows partition is formatted.  If I remember correctly, FAT32 doesn't support duel booting.  If it's NTFS, you can duel boot, as long as you didn't format that partition when you installed Ubuntu.    You need to look at how your disk is partitioned...

---

### Post by expatCM on 2007-11-08
This video is quite good and may help you understand the overall picture ....
[http://video.google.com/videoplay?docid=-6104490811311898236&q=install+ubuntu+xp+dual+boot&total=4&start=0&num=100&so=0&type=search&plindex=2](http://video.google.com/videoplay?docid=-6104490811311898236&q=install+ubuntu+xp+dual+boot&total=4&start=0&num=100&so=0&type=search&plindex=2)

---

### Post by oilchangeguy on 2007-11-08
> **mummra1 said:**
> It depends on how your windows partition is formatted.  If I remember correctly, FAT32 doesn't support duel booting.  If it's NTFS, you can duel boot, as long as you didn't format that partition when you installed Ubuntu.    You need to look at how your disk is partitioned...

the file system of the partiton has nothing to do with the computers ability to dual boot. sharing files is another thing. but dual booting is no problem. the user most likely choose the option to overwrite the entire disk. hopefully the user did a backup of important data BEFORE trying to install ubuntu.

---

### Post by Hayden on 2007-11-08
In terminal use 'sudo fdisk -l' it will list your partitions.

---

### Post by c-2-6 on 2007-11-08
Thanks for all the advice and info, I'll have to reinstall xp per the video, for dual boot. Luckily I didn't lose ony of the files or programs that were on xp. [I] should have read up on the install BEFORE going ahead.

---

### Post by DaveTap on 2007-11-08
If you installed and let it overwrite your disk, then windows is gone and you will have to re-install it, but thats probably a good thing since a fresh install runs mush better :) at least for a little while. :(

Unfortunately Windows does not play well with other systems pre-installed :mad: so it is much easier to install Windows on the whole hard drive, then run defrag to compress everything, and use a program like Partition Magic to make space for your Ubuntu install. 
If its a big hard drive (over 40GB) you might want to add another partition for trying other versions of Linux and/or set up Extended partitions for sharing files. Ubuntu can read and write to your windows partition... but windows can't read or write to Linux... unless you use Fat32 or NTFS
Once you have an empty partition insert your Ubuntu CD, reboot, pick the empty partition and let Ubuntu format the space

---

### Post by oilchangeguy on 2007-11-08
> **DaveTap said:**
> If you installed and let it overwrite your disk, then windows is gone and you will have to re-install it, but thats probably a good thing since a fresh install runs mush better :) at least for a little while. :(

Unfortunately Windows does not play well with other systems pre-installed :mad: so it is much easier to install Windows on the whole hard drive, then run defrag to compress everything, and use a program like Partition Magic to make space for your Ubuntu install. 
If its a big hard drive (over 40GB) you might want to add another partition for trying other versions of Linux and/or set up Extended partitions for sharing files. Ubuntu can read and write to your windows partition... but windows can't read or write to Linux... unless you use Fat32 or NTFS
Once you have an empty partition insert your Ubuntu CD, reboot, pick the empty partition and let Ubuntu format the space

please explain why the user needs partition magic. when ubuntu comes with gparted.

---

### Post by c-2-6 on 2007-11-08
Something I didn't mention is that I have 2 hard drives, the original 20g and a slaved 120g. I believe ubuntu installed on the 20g displacing xp. Can I reinstall xp on the other hard drive and then choose which I boot from?

---

### Post by antony11 on 2007-11-08
Yes - you can install on a seperate drive - but Im not sure how to configure grub for it. You will need to get further help from an experienced linux user (Im a newbee like you).
Ive seen an article on doing what you want but I cant remember where. Good luck

---

