---
title: "Partition Problem during Gusty Install: Only get 2 options: guided-full or manual"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by econmit on 2007-10-22
Hi Folks,

I am new to Ubuntu. I currently have Windows XP on an 80GB HD. I want to install Ubuntu 7.10 as a dual boot, keeping my old windows just in case for now.

With the live CD I try to install and get to step 4...

At that point I do not get the option for a "guided resize" partition that lets me choose the size of the partition. I can only use the entire 80G HD and the manual partition options. But I don't know how to use the latter. I don't want to use the former since I want to keep windows and dual boot.

What is going on? Why don't I get the resize option?

I am really excited about getting Ubuntu 7.10 but I am stuck at this point. Please help. Thanks!

---

### Post by Pumalite on 2007-10-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by econmit on 2007-10-22
Thanks, but these links don't really address my problem. 

The first two (I had already read and) in fact presume I will get the option that I am complaining for not getting!

The third link doesn't fit my situation either. It is about installing Vista from scratch (and making partition decisions in the process), whereas I have already had XP installed on my HD for years.

So thanks, but these links don't provide a solution really.

Any other ideas?

---

### Post by ckamc on 2007-10-22
Well do you have any free space that has yet to be partitioned? If your whole 80GB hard drive is allocated to windows xp then you either need a another hard drive or reinstall XP.

In which you would have to delete the partition of 80GB and reduce whats is allocated to windows xp to less than 80GB, maybe 70 or 60GB to allow a different filesystem (ext3) to install since you can not use windows filesystem (ntfs) for linux.

---

### Post by econmit on 2007-10-22
Thanks. 

I see, So this missing option I was mentioning is really only for those with some unpartitioned part of their HD? hardly a likely situation for people that are considering a switch from Windows without a fresh install. I thought part of the Ubuntu install process would help me through that, but apparently it does not.

OK, so now wow do I reduce the XP partition then? Thanks again!

---

### Post by mivo on 2007-10-22
If you have only one partition currently that Windows lives in, you need to resize the Windows partition to make room for Ubuntu/Linux (to be more exact: to make room to create additional partitions). The arguably best tool for this task is GParted. GParted works for resizing and partitioning. You can download a Live CD to do this [here]("http://gparted.sourceforge.net/livecd.php"). Before you do this, you **must** defrag the Windows partition, ideally twice. It is highly recommend to backup important files, as well. While it is not likely that the process of resizing will cause a loss of data, it is not entirely free of risk. So, do make backups. Defragging the disk will take some time (this is something you will never have to do in Linux), but it is essential before resizing.

An alternative is buying an inexpensive, small hard-drive and add it to your computer.

---

### Post by Maestro23 on 2007-10-22
> **mivo said:**
> If you have only one partition currently that Windows lives in, you need to resize the Windows partition to make room for Ubuntu/Linux (to be more exact: to make room to create additional partitions). The arguably best tool for this task is GParted. GParted works for resizing and partitioning. You can download a Live CD to do this [here]("http://gparted.sourceforge.net/livecd.php"). Before you do this, you **must** defrag the Windows partition, ideally twice. It is highly recommend to backup important files, as well. While it is not likely that the process of resizing will cause a loss of data, it is not entirely free of risk. So, do make backups. Defragging the disk will take some time (this is something you will never have to do in Linux), but it is essential before resizing.

An alternative is buying an inexpensive, small hard-drive and add it to your computer.

Getting ready to post the same process, mivo. Very important to defrag that Windows partition 1st before resizing, due to how Windows stores its files.

---

