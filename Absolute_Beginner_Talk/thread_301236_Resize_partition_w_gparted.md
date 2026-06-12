---
title: "Resize partition w/ gparted"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-11-16
Hello,

I had a partition that was 28.88 GB that I just put mp3's and jpegs on. I also have a partition with Windows and one with Ubuntu that are both 22 GB. I ran gparted from my live CD and deleted the shared files partition that was 28.88 GB and now it is listed as being 'unallocated'.  I would like to make my partition with my ubuntu installation larger by using this unallocated space.  When I go to resize the Ubuntu partition, gparted will not let me increase the size becuase it says I have no free space preceding it. 

Did I do something wrong? How can I resize my Ubuntu installation to 50 GB with how I have it at it's current state with gparted?

I look forward to a soloution..

~Andrew

---

### Post by wieman01 on 2006-11-16
Does the free space come _after_ your Ubuntu install or is it _before_ your Linux partition? It's best if you attached a screenshot of GParted... Then it easier to advice. But this should not be a big problem.

---

### Post by andrew222 on 2006-11-16
Thank you for reply and help wieman01,

A screenshot is attached to this reply and I would make an educated guess to say that my Ubuntu partition is probably before the unallocated space. 

Glad to hear it isn't a serious problem and look forward to solving this problem.

Andrew

---

### Post by andrew222 on 2006-11-16
Sorry, I didn't attach the screenshot to the last post so here it is...

---

### Post by wieman01 on 2006-11-16
Oh well, this is a bit more complicated that it seemed, because the unallocated space is on an extended partition together with SWAP. So we have to do a bit of housekeeping & have to adjust "/etc/fstab". Are you ready for that?

This will be a bit ugly now, and we'll have to get our hands a bit dirty, but I have been through the same thing. First thing we need to do is move SWAP from the extended partition.

1. Resize "/dev/hda2" and free up 1 GB for the new SWAP partition.
2. Format the unallocated space following "/dev/hda2" and choose SWAP as volume format.
3. Open this file & post the contents:
> sudo gedit /etc/fstab
Then I will show you what you need to change in "fstab". Once we have done that you need to reboot & see if the changes stick. If they do, we go back to the Live System (CD).

Got that?

_**EDIT:**_
Please tell me what the label (number) of the new SWAP partition is.

---

