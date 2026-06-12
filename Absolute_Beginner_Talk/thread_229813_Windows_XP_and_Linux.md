---
title: "Windows XP and Linux"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by BenWynn on 2006-08-05
Hey Guys,

Ive read on the forum a way to run XP and Linux on the same Dual Boot Computer but to be honest it is way to compicated for me to undersand to being a Computer wizz. Could Somebody tell me a simple way or atleast explain what all that means!!


Ben

---

### Post by benuski on 2006-08-05
You can use the partitioner that comes with Ubuntu livecd to make your hard drive into 2 separate chunks.  One of these you can keep using windows xp on, and the other you can install Ubuntu one.  Also, the installer installs a boot loader known as GRUB that allows you, everytime you start your computer, to choose between loading Windows or Ubuntu.  If you need more detailed instructions on how to do it during the livecd process, I'm sure we can help.

---

### Post by MiThRaZoR on 2006-08-05
I'm not a big computer genious, but on MS-DOS you can partition your hard drive. So just do it there or better yet, use partition magic and partion however much you want for Ubuntu.

While you're installing it, I'm sure if you pay attention closely you'll know when to do what.

---

### Post by aysiu on 2006-08-05
Imagine you have a two-car garage. Right now, though, it's a very large one-car garage... and you have only one car.

So the first thing you have to do is make room for the other car (move all the extra crap--hockey sticks, knitting yarn balls, firewood--to the corner). Then, you drive the new car into one side, right next to the old car. Finally, you fix your garage door opener so that if you press one button, it opens the door to your old car, and if you press the other button, it opens the door to your new car.

In other words:
1. Defragment.
2. Repartition.
3. Install Ubuntu on one partition.
4. Install Grub to the MBR.
5. At the Grub menu, select either Windows XP or Ubuntu by pressing the up or down arrows.

Oh, and don't forget 0. **Back up all your data**.

Some helpful links:
Partition planning - [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
Downloading and burning Ubuntu - [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)
Installing a dual-boot with the **Alternate CD** - [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
Installing a dual-boot with the **Desktop CD** - [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

And don't forget that you can try Ubuntu without even installing it. The Desktop CD can run a "live" session that is off the CD and your computer's RAM. It does not affect your hard drive.

---

### Post by BenWynn on 2006-08-05
Thanks guys for all your help!!

---

### Post by deanlinkous on 2006-08-05
aysiu - I love that explaination! Even better than the box or records, put a divider in the box...etc...

---

### Post by woodlandjustin on 2006-08-05
I just installed Ubuntu, so everything was wiped and only there is Ubuntu. I want Windows XP too. Do I have to start from the beginning again, partitioning the harddrive and then reinstalling Ubuntu, then Windows? Or can I just make some space here from Ubuntu and the install Windows without reinstalling Ubuntu?
Thanks
Justin

---

### Post by RawMustard on 2006-08-05
I'm pretty sure you have to install windows first on your first partition, then Ubuntu on the freespace on your second partition.

Also I don't use grub boot manager to boot windows, instead I use windows boot manager to boot Ubuntu.  That way if I ever have to install windows again, I don't have to worry about re-installing grub.

Here's a link that explains how to do that.
[http://www.tprthai.net/bootmgr.htm](http://www.tprthai.net/bootmgr.htm)

---

### Post by deanlinkous on 2006-08-05
Easiest to install windows first, ubuntu second. But it is possible to go the other route but I wouldn't suggest it. As RawMustard said you CAN use the windows boot manager to boot ubuntu. In this case you COULD install ubuntu second and make it work. But if you want less headache then just start over if possible. :) That how-to seems a bit overcomplicated to me or at least it sounds harder than it really is IMO.

---

### Post by PaulFXH on 2006-08-05
Hi Ben
I set up a dual boot system with WinXP and Ubuntu two weeks ago for the first time.
While it sounds intimidating, I can honestly say it is a piece of cake. Once you have done it, you'll wonder why you had thought it was so complicated.
While I did quite a bit of reading before I started, I found this video on dual booting to be excellentand genuinely helped me a lot.

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

However, it would be as well to watch it at least a few times as these are experienced guys and perhaps overlook what could be a daunting task for a newbie.

Good luck

Paul

---

