---
title: "Created a seperate home partion &amp; nothing works now"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by captgadget on 2008-01-27
I followed the steps in Linux Format magazine to create a partition and moved my home folder that partition. Then when I tried to use applications it couldn't find the home directory. Now, I got it to work by edit fstab but now none of the other disks will mount. Can anyone tell me how to move my home directory back to the original spot?

---

### Post by cmnorton on 2008-01-27
Does this involve a second disk? I would be interested in why you moved the partition, if you did not want to move it to another hard drive.

I move my home partition, because my first hard drive was 40GB, and I wanted to move home to the second drive, a 200GB.

To fix this: 

1) Boot with the live CD, and make sure you can see your home directory, wherever you put it. 

2) Using sudo, mv the home directory back to /.

3) If this is on a second hard-drive, then why not complete the move?

[http://ubuntuforums.org/showthread.php?t=674328](http://ubuntuforums.org/showthread.php?t=674328)

and there are other links for mounting a second drive; just search the forums for them.

---

