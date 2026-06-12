---
title: "Finally installing Ubuntu."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Ghozt on 2006-06-15
I'm sick of windows and want something new, enough said.
I have Paragon Partition Manager Pro installed, and I want to make a new partition on my drive for ubuntu, so that I can dual boot with windows & ubuntu.

I tried to install ubuntu about an hour ago, hoping it would have an option for creating a new partition and installing it there, but I didn't see one. Does anyone have any experience with Paragon, or is there a partition option with Ubuntu that I'm just not seeing?

Edit: I just looked at my old thread, and someone posted a link for setting it up. If anyone else has comments though please post. Thanks

---

### Post by Sutekh on 2006-06-15
Ubuntu uses a partitioner during the installation; parted if you use the traditional text install from the Install/Alternate CD and GParted if you use the Live/Desktop CD.

You shouldn't need any other partitioner.

Try this link for help on using the text installer

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Try this link for help on using the graphical installer

[http://www.psychocats.net/ubuntu/windowstoubuntu.html]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")

---

### Post by muep on 2006-06-15
If your Windows install uses the NTFS file system like WinXP usually does, Ubuntu won't be able to resize it, except for the livecd. In the livecd you probably first need to install ntfsprogs with:
```
sudo apt-get install ntfsprogs
```

It would be easier to leave some unpartitioned space on the disk with your partition manager that you already are familiar with. Ubuntu should detect this unpartitioned space and install itself there.

---

