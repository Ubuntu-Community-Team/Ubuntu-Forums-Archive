---
title: "Mac G4"
date: 2005-02-13
forum: Apple PPC Users
---

### Post by ratcat1 on 2005-02-13
I plan to install Ubuntu to a partition on my G 4 400 AGP with ATI Rage 16meg, 1 gig ram. 
Does Panther or Ubuntu go on the first partition? 
The mac is for design work at 1280x1024 and larger, millions colors. Will Ubuntu run at these settings? The color calibrated  settings cannot and will not be changed. 
I want to replace the PIG MS Office with OOo. Will Ubuntu see the Epson R200 printer? 
Thanks!

---

### Post by emperor on 2005-02-13
Here what felllow Ubuntu PPC users have to say:
 [http://www.ubuntuforums.org/showthread.php?t=4017&highlight=PPC+howto](http://www.ubuntuforums.org/showthread.php?t=4017&highlight=PPC+howto)
 
 The guys at Yellow Dog would say to make a free partion at the beginning and a then a new HFS+ pariton for OSX. Then reinstall OSX prior to installing Yellow Dog. For example:
 
 "Using the OS X CD run disk utility and make two partitions. Put OS X on the second one. I formatted the first partition as extended, but NOT journalled. Then I installed OS X to my tastes. Next I rebooted with YDL in. Since I knew how big a partition I left for YDL I didn't need to know the hda number but you may need that. I then in a roundabout fashion used disk druid, deleted the extended partition and went back and out of order from the instructions YDL supplies which didn't work, I assigned the bootstrap part for 1 meg, the rest of the part for YDL/root then had to reedit that part to make the swap section of 512 mb. This was the only way it would accept the parts that needed to be made."
  
"So now on boot up you have just a second or two to decide what to boot from, YDL, OSX or a CD. YDL is the default. More importantly I am running OS X natively. Maybe I'll try an figure out how to edit that loader to change the order and timeout on it. It's gotta be possible."
 
 [http://www.yellowdog-board.com/viewtopic.php?t=447](http://www.yellowdog-board.com/viewtopic.php?t=447)

---

### Post by chascon on 2005-02-16
"Does Panther or Ubuntu go on the first partition? "
Doesn't really matter.  I have OS X on my first partition and ubuntu after.  The problem is that OS X's disk utility will only allow you to put an HFS+ first else the partition scheme collapses.
But I wanted a HFS+ first, that means on top, while a Freepartition after/underneath.    So what I believe I did was create two HFS+ partitions, then openbsd installed onto that.  In the end I took debian installer to delete that openbsd partition for debian.  Thus, you don't need to install FreeSpace first/top.  

I ***ume the debian/ubuntu installer can format a HFS+ partition if you make two HFS+ partitions rather than making one FreeSpace partition up top/first, and a HFS+ after/bottom.

So there, you don't have to install HFS+ after/bottom of a partition designated for a latter gnu-linux install.

PS-I believe that this question was already answered prior.  Please serch forums so as to not create duplicates.  Although, I've made error myself when I haven't been able to find something.

---

