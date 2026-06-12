---
title: "Installing 7.10 on external hard drive"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-11-17
--------------------------------------------------------------------------------

Thank you both very much. I wiped the disk and burned it again at 4x, last time I burned it at 10x. Lol. I am actually in the middle of the installation right now, and am trying to get it onto an external hard drive. Im an too worried about wipping my internal hard drive and was hoping someone could help me along from where I am, and give me a heads up. right now I am choosing a partition, which I chose 92% of the hard drive which is 100.8 gigs. I then chose guided - resize SCSI8 (0
I now have a list of devices to choose from, one has winodws, one is a recovery, and the last is the external. Here is my list.

/dev/sda
/dev/sda2 fat32 /media/sda2 - 7345mb 3200mb
/dev/sda1 ntfs /media/sda1 - 112678mb 51600mb
free space - 8mb
/dev/sdb
/dev/sdb1 - 120031mb 33mb

I have nothing on the external hard drive except preinstalled software from the company. Is the bottom one the one I want to choose. Is there anything Ive done wrong or special I should do to make it work for the external hard drive. Thanks to anyone that answers my extremely noobish questions.

---

### Post by Inxsible on 2007-11-17
yes, your sdb is most likely your external drive. You can create partitions in it and install it there.

---

