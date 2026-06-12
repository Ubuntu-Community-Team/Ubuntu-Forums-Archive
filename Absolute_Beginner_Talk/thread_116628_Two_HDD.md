---
title: "Two HDD"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-01-13
I've installed Ubuntu and all works. My PC has 2 HDDs and Ubuntu set up the primary during install. If I go to Disks via the Desktop (as root), it can find the secondary HDD but will not allow me to set up any partitions on it. Why is that?

---

### Post by Jimmey on 2006-01-13
I'm not sure - Try getting Gparted. If you've the internet on your Ubuntu box, in the terminal, type
> sudo apt-get install gparted
If you've not already got it.

Hope it helps.

---

### Post by cotcot on 2006-01-13
Try with "parted" or "Gparted"  from the Ubuntu LIVE CD . (or QT parted from another live CD such as Knoppix when Gparted gives a segmenation error).

In terminal : sudo parted
Then : print /dev/hdb. This lists what you have. There is a good manual for parted. (google "parted manual")

Hope this helps you a bit

---

### Post by My-dial-up on 2006-01-16
Gparted worked a treat.

Many thanks.

---

