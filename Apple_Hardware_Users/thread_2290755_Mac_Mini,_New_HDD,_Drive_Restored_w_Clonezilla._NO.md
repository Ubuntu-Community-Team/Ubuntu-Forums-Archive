---
title: "Mac Mini, New HDD, Drive Restored w Clonezilla. NO BOOT!"
date: 2015-08-15
forum: Apple Hardware Users
---

### Post by typo-joe on 2015-08-15
I've got a Mac Mini (2007). It is used as a media server.  I recently just bought a new hard drive (1 TB) and new ram (3 GB).  Before installing everything, I made a clone of the original drive and put it on an external drive.  I swopped out the hdd and the ram, booted with clonezilla, but it wouldn't recognize my external drive. So I installed the basic install of ubuntu server, mainly to partition the new drive, thinking that might be my problem. 

As soon as the install finished, when it asked to reboot, I reinserted the clonezilla flash drive and rebooted into it. Never booting into the basic (clean) install I just installed.  Clonezilla comes up, I go through all steps, it sees the external drive, copies everything over, erasing everything that was on the new drive (which was the basic install I just put on there). Everything was going great, so I thought.

When I rebooted, I end up with a the flashing folder-with-a-question-mark icon. Which indicates it can't find a drive to boot from.

I booted from the install disk for ubuntu server and used the boot from local drive option (not sure of the actual name). My understanding, it tells it to boot from the hdd instead of the disk. It booted up, like before the swop. Logged in, checked the drive with df -h and it showed everything just as if the old drive was still in there. 67% used of 80 GB (yeah it was small). I was able to ls around some of the directories and all my media was there.  Great sign.

I end up booting from the install disk again and run the repair mode.  Ended up trying one or two things in there, not really sure what off the top of my head.

After another attempt at booting, same blinking icon.  This attempt was with no disks, no usb drives, etc. plugged in or inserted... just the new hdd.

Also worth mentioning, although I'm sure obvious, when booting holding shift, the only option ever shown is whatever the other option is (the usb drive or cd). Normally, as you know, you'd see at least two options, the installed and the attached or inserted.

Is this a rEFIt issue?  I'm wishing I would have installed mac os x to begin with. Installed rEFIt (or the like) and then put the back up clone image onto the drive.  I feel this would have avoided these issues.

Any help would be greatly appreciated. Sorry if I rambled.

---

### Post by typo-joe on 2015-08-15
Well I don't think it's the rEFIt issue I was worried about.  I went ahead and reformatted the new drive and installed a clean copy of Ubuntu Server. However, this time after installation, I did reboot into the newly installed os, with no issue.... lol, well, other than its not my backup.

So this leads me to believe its something with the clone image or how its being rewritten on the new drive.  I did realize that when I installed the basic install before, I used Entire Disk with LVM (or whatever its called). I don't believe I did that on the original drive.  I don't know what it is, but wondering if that may have something to do with it. Truthfully, I grasping at this point.

Although rewritting the clone would be the best scenario, I might have to start looking into redoing the media server set up and figuring out how to snag only the media files off the backup.  IDK, I'm not giving up on the clone just yet.

On a positive note, it sure was nice to see over 900gb available.  Can't wait til I get her back up and running!

---

### Post by JohnAtilano on 2015-08-18
I had a similar problem a few years back. Using "dd" to clone your drive should work. You'll then need to use Gparted to expand your partitions. I wrote a blog post so I wouldn't forget how I did it. Link below. Give it a shot. 

[http://johnatilano.com/2011/05/21/53270156/](http://johnatilano.com/2011/05/21/53270156/)

---

