---
title: "Asus 1015e (Ubuntu Version): Recovery Partitions"
date: 2013-09-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by gaussian on 2013-09-25
Just received yesterday my Asus 1015E with Ubuntu 12.04 preinstalled. Love the computer so far.

It is advertised as having a 320G drive. I don't need that much space in my device and could live with the current configuration, but the configuration is weird. Does anyone more knowledgeable have this computer and can make sense of this? Gparted gives me the following information:
```

/dev/sda1 fat32   mounted at /boot/efi 95Mb partition, with 1Mb used
/dev/sda2 fat32   not mounted automatically 3.73Gb partition, Label "PQSERVICE", 3.73Gb partition, with 2.53GB used
/dev/sda3 ext3    mounted at /, 178.85Gb, originally little over 3Gb used
/dev/sda4 unknown clearly the swap partition, 7.45Gb
/dev/sda5 ntfs     not mounted, 107Gb, 3Gb used partition

```
What puzzles me is the last partition. Why would a computer be delivered with 107Gb partition with no apparent use for an average user? I am assuming that the /dev/sda2 is the recovery partition, at least the contents of it look like that. When I am mount /dev/sda4 there does not appear to be any files on it. Can I just format it over or move my swap and resize my root partition to take that space? I want to keep the recovery partition at least for now since you might never know if you have to send the computer for service. Any thoughts?

---

### Post by Dreamer Fithp Apprentice on 2013-09-26
It seems to me you nailed it - that IS weird indeed. I'd drop them an email and ask them to explain it. Somebody may have had the idea of the last partition being a data partition, a practise I strongly advocate, but why on earth would they use NTFS on a pure linux machine? 

I could be wrong and I can't easily check it because I don't use a swap partition but I would expect gparted to have no trouble identifying a swap partition. Maybe someone who uses one can comment. If it isn't a swap I would suspect either it is simply unused or possibly encrypted.  Could this be someone's used drive rather than a new one?

---

### Post by gaussian on 2013-09-26
> **Dreamer Fithp Apprentice said:**
> It seems to me you nailed it - that IS weird indeed. I'd drop them an email and ask them to explain it. Somebody may have had the idea of the last partition being a data partition, a practise I strongly advocate, but why on earth would they use NTFS on a pure linux machine? 

I could be wrong and I can't easily check it because I don't use a swap partition but I would expect gparted to have no trouble identifying a swap partition. Maybe someone who uses one can comment. If it isn't a swap I would suspect either it is simply unused or possibly encrypted.  Could this be someone's used drive rather than a new one?

Thanks. I have contacted ASUS and will reply in this thread if I hear anything from them about this. I think it is supposed to be a data partition as well.

---

### Post by gaussian on 2013-10-03
Just a quick update. I went through an exchange with an Asus support person to convince her that my laptop truly came with Linux preinstalled. Not very shocking, I bet the share of linux preinstalled laptops is tiny. Following that my inquiry got forwarded to a "special team in their support department" and I have been waiting to hear back ever since.

---

### Post by Dreamer Fithp Apprentice on 2013-10-06
I'm afraid that is typical of tech support in the IT arena. I suppose it is because computers went from being something only us weird people bought to being a standard item in every household so fast that there aren't many qualified people and most of the complaints are kindergarden level anyway. So they have a recipe book and look up the quiestion and read the prepared answer while pretending they know what all the words mean. Not a good sign for them to take so long. I'll be a bit leary of buying from them in the future and I thank you for the information. Sounds to me like they gave you a used drive and didn't partition and format it properly. Or whoever did it is just plain incompetent. Good luck.

---

### Post by wn1ytw on 2013-10-06
I had that problem with that laptop and fixed it by following this reply:

[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)


That link will provide information on how to properly align partitions. Whether it is an SSD or Mechanical drive. There is nothing wrong with the drive, it is simply a partitioning error. A copy of the g-parted boot disc will help a lot with this. Which can be found at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

I installed and ran Gparted which allowed me to realigned the 5th partition that was misaligned as the above refers to. 
GL scott

EDIT I think it had something to do with the laptop also being shipped in a version with winderz 8 then they just added partitions?

---

### Post by gaussian on 2013-10-12
Just an update:
1) Asus never got back to me, it has now been over week and a half since they promised that somebody from the "special support team" will get back to me. Unrelated complaint: their support website has to be the slowest website I have ever used, just in terms of load/response times when browsing.

2) I believe now that this is a simple partitioning error. I can easily fix it, but at the moment I am not going to bother. My 177Gb partition is not even half full so I don't expect to ever need the extra space. The purpose of this computer for me is to be a web browsing device and device to show slides when teaching.

3) Thanks for the tips on how to use Gparted. If anyone else has the same problem, you basically have two options:
a) format over the NTFS partition and make it a data partition. This is relatively quick and almost risk free. Backing up important stuff before playing with partitions is always a good idea.
b) Remove the partition altogether, move the swap partition and resize the original root partition. This is quite slow and little riskier, since you will be touching the root partition. For this you'd also need a USB stick to boot from, you cannot resize the root partition while it is in use.

---

### Post by aquanauta on 2013-12-24
Hi, can you please explain with more detail how to fix the Asus/Ubuntu partition issue? Thank you. Merry Christmas!

---

### Post by oldfred on 2013-12-24
@cmayle
Is yours a Ubuntu only system? What issue do you have? 

Post this:
 sudo parted /dev/sda unit s print

---

### Post by aquanauta on 2013-12-24
-

---

### Post by zococo on 2014-01-31
Hi,
Just received my new asus 1015E and have the same partitions.

---

