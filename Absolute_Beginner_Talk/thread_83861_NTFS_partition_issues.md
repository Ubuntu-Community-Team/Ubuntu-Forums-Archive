---
title: "NTFS partition issues"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by isaacf on 2005-10-29
I've been attempting to install ubuntu. I have a 30GB harddrive and Windows XP Pro SP2. I defragged with the windows tool and the O&O defrag tool several times. I followed the guide on users.bigpond.net.au/hermanzone and the installer kept looping me back, so I defragged some more and it still didn't work. I then lurked on these forums and tried to partition it with qtparted off of Knoppix and that also failed. On every partition tool, when it showed my current partitions, it didn't recoognize any of my data. I have 18GB free and the installer and qtparted kept saying I had nothing on there. Please help.

---

### Post by aysiu on 2005-10-29
The best free partitioning tool I've ever used is Mandriva's DiskDrake. I don't use Mandriva, but I use DiskDrake (use the Mandriva installer up to the partitioning process--then I reboot and use the installer CD of the distro I really want to install). Otherwise, for nonfree and costly, you can try Partition Magic.

---

### Post by isaacf on 2005-11-02
Okay. I downloaded disc 1 of the Mandriva installer and ran it, and when I got to the partitioner, I selected my Windows partition and clicked resize, but it gave me a message saying ntfsresize failed. Is there anything else I can try?

---

### Post by aysiu on 2005-11-02
Have you tried defragmenting your NTFS partition before resizing? You'll have to defragment in Windows.

---

### Post by isaacf on 2005-11-02
[QUOTE=isaacf] I defragged with the windows tool and the O&O defrag tool several times.[/QUOTE]

Each time I have attempted to partition, I have defragged two more times just to be sure.

---

