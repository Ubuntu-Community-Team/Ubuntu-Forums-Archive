---
title: "Changing SWAP Partitions"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-07-30
Hello,

Somehow a few months ago when I installed Ubuntu I gave my SWAP Partition just over 9GB and my "/" partition 8GB. I know it is stupid of me. 	#-o

Now that time has passed I have started to fill up my "/" Partition. Since my swap space is running at around 33MB(.3%) most of the time I was wondering if I could take some of that space and add it to the "/". 

I heard though that you can't resize ext3 file systems, is this true?
If I can't cut into my Swap space, could I cut into my Vista or XP partitions?
And (finally) what does the swap partition do? I am interested :D

Thanks,
tprzepiorka

---

### Post by bodhi.zazen on 2007-07-30
Yes, you can resize your partitions with gparted. Best to do from a live CD like gparted live :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

You can use the ubuntu live CD, but you might have problems depending on your disk geometry...

Also the ubutnu CD will mount your swap, so you will need to unmount it first with :

sudo swapoff </dev/hdxy>

---

