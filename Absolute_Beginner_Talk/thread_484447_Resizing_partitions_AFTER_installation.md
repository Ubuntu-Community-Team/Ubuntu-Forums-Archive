---
title: "Resizing partitions AFTER installation"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by jasonrandolph on 2007-06-25
Is it possible to resize partitions after you have been using Ubuntu for a while?  I'm finding that I'm using Windows a lot less than I anticipated, and I don't want to lose all the tweaks I've made to Ubuntu be reinstalling it.  Thanks for any help you can give me.

---

### Post by wjp.reg on 2007-06-25
> **jasonrandolph said:**
> Is it possible to resize partitions after you have been using Ubuntu for a while?  I'm finding that I'm using Windows a lot less than I anticipated, and I don't want to lose all the tweaks I've made to Ubuntu be reinstalling it.  Thanks for any help you can give me.

It depends partly on the layout of your HD that you have now.  You can shrink Windows using gparted but you cannot move the free space around, only add it to the next contiguous partition, or so I have found. 

Make a good image backup before you do anything.  I used the gparted live cd.

good luck

---

### Post by BobCFC on 2007-06-25
You have to unmount a partition to shrink or grow it.  If you are having trouble because system partitions are in use you might want to try the [gparted livecd]("http://gparted.sourceforge.net/livecd.php") it is only a 50mb .iso to download then burn to a cd.

Then you can reboot and change system partitions while not in use because the livecd is a mini linux distro dedicated to gparted.

---

### Post by catnappist on 2007-06-25
Not meaning to give any advice from a totally new Ubuntu rookie, but I started out with a root of 2GB like the instructions said.  Naturally I had to add to it within a day before I understood what the root was.  I had already downloaded a system rescue CD. Didn't have any trouble absorbing the area before it. On the other hand, the area before it wasn't connected to my Windows XP.  On the third hand (I've got a million of 'em!), it didn't mess up my first good installation of Feisty Fawn either. I don't think you can screw up with the system rescue CD unless you really want to, but it can be a little stubborn sometimes.

---

### Post by catnappist on 2007-06-25
On the fourth hand, I would make sure I defragged Windows first...!

Cheers.

---

### Post by bodhi.zazen on 2007-06-25
> **wjp.reg said:**
> It depends partly on the layout of your HD that you have now.  You can shrink Windows using gparted but you cannot move the free space around, only add it to the next contiguous partition, or so I have found. 

Make a good image backup before you do anything.  I used the gparted live cd.

good luck

You can resize, move, copy, paste, etc with the gparted CD.With the newest gpated CD I think does not have the limitation your are referring to in terms of free space.

---

### Post by rillip on 2007-06-25
If you have a typical hard drive format, where Windows comes in the partition BEFORE Linux, then you should be able to defrag and steal the partition space with no problem, because your next partition is a Linux one.  You may end up resizing the Windows, then your swap, then your root or home (wherver you want to put the space) in order to do it, but I've resized several times and never had an issue with data loss.  There is the potential it can happen, but in half a dozen resizes, I've had zero errors introduced.

So in short, yes. I did the same thing, as a matter of fact.

---

### Post by wjp.reg on 2007-06-26
Here is a review of gparted as tested.

[http://techgage.com/article/gparted_livecd_31-1]("http://techgage.com/article/gparted_livecd_31-1")

---

### Post by carloslosgrande on 2007-06-26
I've done exactly as you are planning, on 3 separate machines without any trouble at all, and as Bodhi Zazen says, the GParted CD can move, resize etc without difficulty. Just do it slowly and in logical order. Before you actually make any change you'll be asked to check.

---

### Post by bodhi.zazen on 2007-06-26
> **wjp.reg said:**
> Here is a review of gparted as tested.

[http://techgage.com/article/gparted_livecd_31-1]("http://techgage.com/article/gparted_livecd_31-1")

Thanks for the link.

---

### Post by catnappist on 2007-06-26
I clicked on the link, read the pitch, looked at the screenshots. Sorry, I thought it looked a little confusing compared to gParted on the system rescue CD. It's about 112M, bigger than the gParted CD by itself, and it has a bunch of other stuff I have no use for. But it's real easy to work and I haven't screwed anything up yet. Here's the link...

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

Cheers!

---

