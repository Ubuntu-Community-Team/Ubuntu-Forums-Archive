---
title: "partimage question"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by paker on 2007-08-04
I have just one hard disk (200 gb), one partition, Feisty. I want to run partimage for system backup.
Can I back up hda1 to hda1? Or should I have created another partition during Feisty installation just for partimage?

IF I need another partition, rather than reinstalling Feisty with 2 partitions, can I somehow use an old slower 30gb hard disk sitting on the shelf?

Thanks.

---

### Post by ayenack on 2007-08-04
You can use the older drive (as you probably know Partimage will compress your files and will only backup used space not the whole partition). This is probably a better solution because it means that your backup drive is separate from your every day use drive. Which means if you ever did a reinstall or disaster strikes you could keep you backups without to many problems.

A thing to consider is your main drive is 200GIG so once you start getting quite a few files on it the 30GIG drive will not be big enough. Might be an idea to buy an external USB drive and use that. If you decide to use the 200GIG drive you can repartition it with GParted.

sudo apt-get install gparted

To install GParted.

Quick question, does Partimage write to local hard drives? I know it'll write to CD/DVD's and across networks to network drives but not to sure it writes to local hard drives. Also If your going to use partimage it's a good idea to download the live CD ([SystemRescueCD]("http://www.sysresccd.org/Main_Page")) as well this could be very useful in times of need.

---

### Post by bodhi.zazen on 2007-08-04
IMO partimage should be run from a live CD not on a mounted / partition.

Yes, partimage will save to a local hard drive.

No you should not save an image of hda1 to hda1 because that would imply hda1 is mounted ...

---

### Post by paker on 2007-08-05
Thank you very much for answering my questions. I just want to backup my system right after fresh install of Feisty, automatix, codecs, and updates. It will not be used for daily/weekly backup. I have already downloaded and burned SystemRescueCD.

---

