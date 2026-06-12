---
title: "problem installing ubuntu (partitioning)"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by papermoon on 2007-08-07
i dont understand how this works... My hard drive has 23 GBs free so i was going to assign a 20GB partition to ubuntu but when i go on the installation it only allows me to create partitions of 50-65 gbs. i am confused T_T

---

### Post by papermoon on 2007-08-07
bump

---

### Post by papermoon on 2007-08-07
anyone?

---

### Post by papermoon on 2007-08-07
is it that when it;s asking me to resize a partition, the partition it is displaying is the windows partition? (i.e. it is telling me 50 GB and leaving the rest to install ubuntu?)

---

### Post by papermoon on 2007-08-07
anyone??????

---

### Post by thefoolisme on 2007-08-07
> **papermoon said:**
> i dont understand how this works... My hard drive has 23 GBs free so i was going to assign a 20GB partition to ubuntu but when i go on the installation it only allows me to create partitions of 50-65 gbs. i am confused T_T

First, it usually takes longer than 10 min for a response.  Bumping every minute, is likely to get your question ignored.

Using gparted, which choice did you make for making partitions?  Is the 23GB of free space at the end of the drive?  If so, I would recommend using the choice concerning creating a partition with the free space at the end of the drive...I'm not in front of a linux machine right now.  

As for your other question about whether it's showing your windows partition...do you have windows installed on your computer?  You didn't say.  Does your windows partition match the size it's saying?  could be an indicator.  BTW, it is recommended that the windows partition be defragged 2-3 times before compressing down.

---

### Post by AlexenderReez on 2007-08-07
> **papermoon said:**
> i dont understand how this works... My hard drive has 23 GBs free so i was going to assign a 20GB partition to ubuntu but when i go on the installation it only allows me to create partitions of 50-65 gbs. i am confused T_T

> **papermoon said:**
> bump

> **papermoon said:**
> anyone?

> **papermoon said:**
> is it that when it;s asking me to resize a partition, the partition it is displaying is the windows partition? (i.e. it is telling me 50 GB and leaving the rest to install ubuntu?)

> **papermoon said:**
> anyone??????

these kind of posts surely give difficult to handle unanswered post ....hm....i guess you choose first option of partitioning right?choose last option,which manual partitioning....so that you can manually create size for partition.....hm....don't forget to make linux swap partition about 512mb :) ....

---

### Post by guguma on 2007-08-07
You can use GPARTED LIVE. Google it and burn it, then you can graphically see what is going on. It will be easier for you. If you are not using a LIVE CD of course. If you are using one then it has GPARTED itself. If you explain it better though I may be able to help

---

### Post by cobrn1 on 2007-08-07
> **guguma said:**
> You can use GPARTED LIVE. Google it and burn it, then you can graphically see what is going on. It will be easier for you. If you are not using a LIVE CD of course. If you are using one then it has GPARTED itself. If you explain it better though I may be able to help

Are you using the liveCD (the normal one) or the alternate install CD (for the text-based install). If you are text-installing then you should download GParted CD and burn the .iso, then use that the graphically mess with the partitions. As said above, if you are using the normal, live cd and graphical ubuntu cd, then GParted is already on it.

I'd stay away from  using the text based installer to set up the partitions, graphical really helps in this aspect of installation...

EDIT: oh yeah, and please don't do the bumping thing every few mins... good answers take time... Give it _atleast_ a few hourc before you bump (although many would tell you to wait atleast 24 hours...

---

