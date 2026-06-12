---
title: "What size partition?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by greenw40 on 2007-03-21
Ive got XP running on a 160G HDD unpartitioned and I would like to install Ubuntu also.  I've been reading some posts on partitioning, and also this site: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).  The only easy option seems to be to limit the windows space and partition the rest of my hdd to use with Ubuntu.  Is there an easy way for me to just partition 5-10G of my 160G Hdd (70G free) to install and use Ubuntu?  The third partition option during the installer seems a little complicated for me since ive never done this before.  Any help would be great.

---

### Post by profXavier on 2007-03-21
First off, I recommend backing up any info you NEED from your system, before you start to partition drives.  Secondly, if you want to partition your drives, without losing data, there is a tool for Windows called Partition Magic. Using Partition Magic, you should do two partitions for Ubuntu, one approx. to 10-13GBs, and another that is the same size as your RAM, for your SWAP.  The larger, 10-13GBs,  should be ext3. You can place it anywhere on the HD you like.

Now, if this doesnt suit you, there is an .exe you can use to install Ubuntu on you Windows computer, the info is at: [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

One more option, to keep you in Windows-land, is to look into VMWare.

---

### Post by greenw40 on 2007-03-21
If I choose the first option when installing (resize free space), can I just slide the bar to make a smaller partition and leave more space for windows?

---

### Post by neji on 2007-03-21
Definitely use the third option, it gives you more control over the size of the partitions. It's not that complicated... just post a question here if there's something you don't understand.

---

### Post by greenw40 on 2007-03-21
Ok so I made two extra partitions on my existing HDD.  One was about 1G for swap and the other was about 12G for the installation for Ubuntu.  Then at the final step I needed to set one as the swap (1G), one as "/" (13G), and the final was "/media/hda1" as default.  Is this normal or is Ubuntu going to overwrite my windows installation?

---

### Post by greenw40 on 2007-03-21
anyone?

---

### Post by Dark Lord Peaches on 2007-03-22
the '/media/hda1' is the partition that windows is currently on, and it should be just fine ive installed kubuntu twice (crashed it the first time) and had no problems

and make sure you have backed up any valuable files just as a precaution

---

### Post by greenw40 on 2007-03-22
So then Ubuntu is installed on the partition labeled "/"?

---

### Post by da1nonlymikeo on 2007-03-22
yes

---

