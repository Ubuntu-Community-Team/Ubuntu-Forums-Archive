---
title: "Trying To Resize Windows Partition With Gparted"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Apt403 on 2007-11-03
When I first installed Ubuntu, I put it on a fairly small (80gb) partition, just to try it. Now I'm using it as my main OS and I need more space on the partition.

I've got a ~150gb partition on my 250gb drive for Windows XP that I want to resize to about 30gb, then resize my 80gb partition with Ubuntu (7.10, BTW) on it to 200gb, using the freed space from the Windows partition.

I tried to use Gparted to resize the partitions, but I was presented with this:

[[IMG]http://img150.imageshack.us/img150/1775/screenshot1se1.th.png[/IMG]](http://img150.imageshack.us/my.php?image=screenshot1se1.png)

Any ideas?

---

### Post by skymera on 2007-11-03
ok i STRONGLY advise tyou to only resize windows.. in WINDOWS!

use partition magic etc.

when i resized my windows in ubuntu, it corrupted and had to reinstall.

just word of advice.

to make it show up, do a disk check in windows :)

---

### Post by Duck2006 on 2007-11-03
Use the live cd of gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Stormspireiv on 2007-11-03
Try going into windows and running chkdsk with the option to recover bad sectors.  You will probably have to reboot to get it to run, then reboot after that.  It would be a good idea to run defrag after that as well.

---

### Post by Apt403 on 2007-11-03
Ran chkdsk, but it didn't find or correct anything. I defragged afterwards, but that didn't help either. 

I would use the Live CD if I could, but I'm out of blanks ATM.

Partition Magic is a bit expensive at $70. Know of any freeware programs that would get the job done?

---

### Post by dgar on 2007-11-03
Is the NTFS partition one of those new fangled 'Dynamic Disk' in the Windows Disk Manager?

---

### Post by Apt403 on 2007-11-03
Nope, basic.

---

### Post by skymera on 2007-11-04
> **Apt403 said:**
> Ran chkdsk, but it didn't find or correct anything. I defragged afterwards, but that didn't help either. 

I would use the Live CD if I could, but I'm out of blanks ATM.

Partition Magic is a bit expensive at $70. Know of any freeware programs that would get the job done?

yes 'expensive'

think out of the box :wink:

---

### Post by Stormspireiv on 2007-11-04
Try installing ntfsfix and running that on /dev/sda1 then boot into windows, shut down, then try gparted.  It seems you are having the same problem I did a while ago, I think there may be bad sectors in your NTFS partition.  If none of the above methods work, you may have to partition from the command line using ntfsresize and fdisk.  That is what I had to do...

---

### Post by Apt403 on 2007-11-04
Huh... It works now! I installed ntfsfix then launched Gparted, just to make sure dev/sda1 is really the Windows partition, and Gparted read the ntfs partiton fine. Just resized it to 30gb. 

Now let's just hope I didn't brick the install. lol

Edit: Well, Windows works fine. Atleast as fine as Windows can...

---

