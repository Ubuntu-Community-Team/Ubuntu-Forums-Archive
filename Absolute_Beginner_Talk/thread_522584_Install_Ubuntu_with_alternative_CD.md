---
title: "Install Ubuntu with alternative CD?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Ukr on 2007-08-10
Hi! Can any body help me to find detailed step-by-step instraction for installation Ubuntu 7.04 with alternative CD? Appreciate for any help! Or, if same have done it before – quick support with patitions on that way.

---

### Post by cobrn1 on 2007-08-10
I would recommend downloading the .iso for GParted CD. This will allow you to graphically modify the partitions, and then you can use the alternate install cd to do everything else. When you get to the partitioning part all you'll have to do is choose whare to mount the partitions (ie, swap, /, /windows, etc) and you won't have to fiddle with the numbers.

Other than that it's quite easy to do. THere are guides if you need (I seem to remember). Google it and see what you find (I think there's an article on psychocats). Good luck.

---

### Post by lyceum on 2007-08-10
I do not know where a step by step guide is, but it is very simple. It asks some questions, you answer and it loads. It is really just like the GUI version, but no mouse and not as pretty.

---

### Post by bodhi.zazen on 2007-08-10
Install form alternate CD: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Ek0nomik on 2007-08-10
The hard part about the Alternate CD if it's your first time installing is using the partitioner.  It's much easier to change partitions graphically, but obviously you aren't able to with the Alternate CD.  Besides partitioning, the rest is a breeze.

When you get to the partitioning phase, you need to type in the size of the partition.  So, if you want a 1.0 GB partition (for /swap perhaps?) you need to type: 1.0 GB, and then accept your changes.

So, you will want to start by creating your EXT3 filesystem (giving it the boot flag, so your computer can boot into this partition), and follow by creating your Swap partition.  (I am assuming you aren't in fear of losing any data) At this point you let it reformat the partitions, thus giving you a clean slate of your hard disk, and then you proceed with accepting the actual installation process.

---

### Post by Ukr on 2007-08-10
Reason I wona try alternative, is my RAM 256Mb, and LiveCD does't go,  it is my first attempt to install Ubuntu 7.04. Before I had 6.10 which was installed with LiveCD, strange!?

---

### Post by bodhi.zazen on 2007-08-10
> **Ek0nomik said:**
> So, you will want to start by creating your EXT3 filesystem (giving it the boot flag, so your computer can boot into this partition), and follow by creating your Swap partition.  (I am assuming you aren't in fear of losing any data) At this point you let it reformat the partitions, thus giving you a clean slate of your hard disk, and then you proceed with accepting the actual installation process.

FYI : Linux does not use the boot flag, that is a Windows thing ;)

---

### Post by Ukr on 2007-08-10
Thanks everyone for help! So, I did / 6Gb,/var9Gb, /swap 1Gb, and /hrome rest - approximately 35Gb, start partitioning and got harddrive indicator lighting continiously, blue monitor ant it is like that for 1/2hr already. Any comments?

---

### Post by bodhi.zazen on 2007-08-10
9 Gb seems large for /var

let it sit ...

---

### Post by mcurtiss1970 on 2007-08-10
i used the automatic partition setting inmy  alt cd install and it was just as easy as the live cd

---

### Post by Ukr on 2007-08-10
I'm waiting, but hard doesn't make any noise,  I dout it doing anythin. One more night not a big deal .Another way to get Ubuntu7.04, install 6.10 and wait till up to dater offer upgreat system to 7.04. That what I've got before. Souds stupid, I just want to know if that Ubuntu7.04 will be the same as intalled from CD?

---

### Post by Ukr on 2007-08-10
**To mcurtiss1970**
i've being reading info HOWTO Install? bafore i start and find that automatic way couse problem in future. The sizes i create is not my idea, exept /var,its realy to big, my mistake, should be around 5GB. Any way i've tryed automatic way - was the same result, i lost my patience at that time, but now i'm waiting.

---

