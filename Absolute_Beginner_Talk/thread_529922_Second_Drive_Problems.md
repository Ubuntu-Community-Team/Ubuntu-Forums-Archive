---
title: "Second Drive Problems"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by old poppa on 2007-08-19
I got a old IBM P3 and installed Ver 6.01.  Had no problems and got pretty familiar with the system. My goal was to create a NAS backup system (to cheap to buy one).  Once again no major problems.  I had install a 80g drive when I first got the system up and running.  After several months I installed a 2nd 160g drive. No problems again, boy did I feel smart.  I ran fdisk -l and I saw the 2nd drive. It also was listed in GParted, so I think it is mounted correctily.  Now here is the problem, I cannot write to the to the directory that it is mounted in, /mnt/store. It is owned by the root.  If I become the root I can write to it.  I tried chown to change owner - not permitted. Tried chmod - not permitted.  Went into the fstab file and tried different option #4 inputs. Went from Default to user,rw but no change.  I have seen other posts with this problems but there was no cure.  Also should the 2nd drive show up in Nautilus like a ext USB drive does. This has been a learning exiperence.  When I had problems with XP, I would ask people at work for help but since I've retired that resource has gone away.  Most friends don't have much computer knowledge - LINUX WHAT?  Well there is my problem hope someone can help me.  Linux seems to be a great system and I will use it when XP goes away, maybe sooner.

---

### Post by TeaSwigger on 2007-08-19
It's a great system. Very flexible. You had to learn Windows so this is just learning some different things. Hang in there and you'll get it.

Can you post your fstab here so folks can review it? Open it in a text editor, copy the text and paste it using the "code" option in the post box, if you're unfamiliar with that. Someone might be able to spot what's going on in it.
 
Yeah sounds like you're on the trail at least; permissions. You should be able to allow a group your ID is a member of to have access. See "man chgrp" in a terminal if you need the info on that. Have to ask, did you try "sudo" in front of the chown / chmod commands?

---

### Post by old poppa on 2007-08-20
Yes I did use sudo.  Found an article after I posted and will try a few more things.  Will post my fstab file later after I try one more thing.  This is really a permission problem.  Thanks for your reply!  UPDATE:  As I was cutting the grass this afternoonI think I will get really up to speed on chmod and chown first.  So for a while the fstab problem will go away.  Last night I also upgraded to 7.04. Of course my problem did not go away but the upgrade was no problem.  Thanks again

---

