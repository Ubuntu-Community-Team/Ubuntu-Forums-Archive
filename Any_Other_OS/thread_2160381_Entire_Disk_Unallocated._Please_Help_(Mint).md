---
title: "Entire Disk Unallocated. Please Help (Mint)"
date: 2013-07-06
forum: Any Other OS
---

### Post by Sly14Cat on 2013-07-06
Hello,
I was trying to install "Mageia Linux" on my computer and it worked. But my filesystem looked odd. My partition I use for storing files and my Windows 7 partition were grouped together. Then there was my Linux Mint then the 3 partitions for Mageia. I found this odd and put the MBR back to normal and now I'm getting this in GParted.

[IMG]http://i44.tinypic.com/2uemqsy.png[/IMG]

In windows, all the different partitions appear but as one huge extended partition. Please can someone tell me how to fix this I've never experieced this problem.

---

### Post by BreezyBrooke on 2013-07-06
You just can't "Revert the MBR" the installalation of Mangeia modified the partitions themselves, reallocating data. So when you put the old MRB back on, nothing it had inside it matched with what the disk was saying, so it then gives an "Unallocated Error" due to it's confusion. Put the old one back or use boot repair to fix it. Someone else here can help you with that as I'm not good at that tool.

---

### Post by Sly14Cat on 2013-07-06
So I reinstall Mangeia?

---

### Post by oldos2er on 2013-07-06
Moved to Other OS/Distro Support.

---

### Post by RadicaX on 2013-07-07
No, do not do that. I am thinking if you reinstall, especially with it doing that, you could overwrite your whole system. What you could do, if you can not wait, is to delete the OS doing it, then reinstall... But since you have messed with the MBR, you might need to repair that before you do that, or it just will do it again. Can you check it out from a live media first perhaps? And do you have any problems booting into your other OSes like Windows? Past that, I can not help you. Remember to have your handy dandy liveCD ready and an empty USB or something to store your photos or anything important on it first.

---

### Post by deadflowr on 2013-07-08
What's the output for 
```
sudo fdisk -l
```

Hopefully, this will give us a far better understanding of the problem than a screenie.

---

