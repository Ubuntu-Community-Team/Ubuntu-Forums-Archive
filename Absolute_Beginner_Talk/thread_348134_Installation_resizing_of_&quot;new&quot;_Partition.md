---
title: "Installation resizing of &quot;new&quot; Partition?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-01-28
Hello,

I am about to install ubuntu on my windows desktop. Obviously I first want to setup a dual boot system. In the installation procedure I now get the question: "How do you want to partition the disc?" with the three options of resizing one partition, erasing the full disc or manually partitioning it.

I have curently 2 partitions on my disc. 1 with windows on it and one with only data. Both are in ntfs. I now want to resize my data partition and with this horizontal bar I can determine the new partition size. But this new partition size, is that the future size of the existing data disc, or of the new partition that will be created on which ubuntu will be installed?

---

### Post by meng on 2007-01-28
Defragment your partitions first, to try to move all the data to the beginning of the partition.
Choose the manual partition, then you'll be able to see exactly what you're doing.

---

### Post by bscbrit on 2007-01-28
At the moment all of your disk space is allocated to windows.  By resizing one of the existing partitions you will make space for your Ubuntu installation.

The space that you use for Ubuntu will probably be split into 2 or more partitions - linux needs different partitions for different functions e.g. the swap partition.  However, it is possible to use a lot of partitions if you wished, one each for /etc, /var, /usr etc.  This is not required - but it is possible.  Asking 10 people how to partition your disk will get you 10 different answers but my own recommendation is that you allocate one partition for /root, another for /home and a third for the swap partition, which should be approximately twice the size of the memory you have installed in the computer.  The advantage of having a separate /home is that you can re-install Ubuntu or another distro entirely without losing all the data that you have saved in your /home directory.  You might even be able to keep some or all of your configuration settings intact between installations :-)

---

### Post by kramer65 on 2007-01-28
ok if you could help me a little bit with that. When I open Gparted i can see one partition on the left in ntfs which is called /dev/hda1 (there's my windows) and on the right a green/blueish box which is (according to the icons) an extended partition with INSIDE of that another ntfs partition (my data part).

Do I need to resize the ntfs that is inside of the extended partion and create the linux partition next to it within the extended partition or do I need to also resize the extended partition and create the new linux partition fully on its own? (it must by in ext3 right)

---

### Post by meng on 2007-01-28
You are correct, it is easiest to choose ext3 for your linux partition.
You could create new partition/s within the extended partition or on their own, it's your choice.
I suggest you create them within the extended partition. Create a swap partition (filesystem type swap) and a root partition (filesystem type ext3). As mentioned earlier, you could also create a separate /home partition (also filesystem type ext3) - that has always been my preference.

---

### Post by kramer65 on 2007-01-28
Ehm... Ok, I was repartitioning. It started, and now I got stuck. I got an error and the whole installation window hangs. It is mainly grey with no information anymore and there is like a prompt that there is an error, but it doesn't say what kind of error..

Is it best to just reboot now or will everything be lost then? On the disk that is being resied I antually have quite some data that I don't want to loose...

Please help!

---

### Post by meng on 2007-01-28
> **kramer65 said:**
> Is it best to just reboot now or will everything be lost then? On the disk that is being resied I antually have quite some data that I don't want to loose...
Okay, in my haste to answer I forgot to mention "the obvious", namely, that you should back up all important data before you do something important like resizing your partitions. If the system has hanged, I would say that you have nothing to lose by rebooting - but you may have already lost/corrupted some data. The GParted partition manager included with the Ubuntu install CD is unfortunately not perfect, but it usually tells you it is unable to complete the task, and does not usually get halfway through the task and then stop.

You may have been lucky and it just told you that it couldn't perform the task. Did you defragment your partitions, as I suggested?

---

### Post by kramer65 on 2007-01-28
Aight thanks.
I'll reboot then. We'll see whats gonna happen. Prolly be back here in a afew minutes..

---

