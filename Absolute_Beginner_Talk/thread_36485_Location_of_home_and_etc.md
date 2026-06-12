---
title: "Location of /home and /etc"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by mjbeam on 2005-05-23
I've read that since I have two hard drives (80gb and 120gb) that it's good to install the system on one drive and /home and /etc on the other. That way if something happens and you end up reinstalling you can reformat the drive with the system on it but /home and /etc will still be intact.

When I initially installed ubuntu I put the system and a 200mb swap on the 80gb HDA and I put home on the 120gb HDB.

Three questions:

1. How do I verify that /home is on HDB?
2. How can I move /etc to HDB?
3. Does doing this make sense?


Thanks...Mike

---

### Post by ola on 2005-05-23
1). You can use df -h (diskfree) where you can se the partitions with mount points.

2). in /etc/fstab  you can set the mount points for all your folders..

3). moving your home folder might be a good thing, but moving etc doesnt make sense to me.. Maybe backup it, but not move it..?

Create partitions makes sense in some cases.. But for mosts installs I would have used the default partitions excepte for the /home folder.. and maybe the /tmp folder (since it allows all people to write to it..)

---

### Post by mjbeam on 2005-05-23
df -h  worked great. Verified that /home is on hdb1.

Haven't tried modifying /etc/fstab since it doesn't make sense to move /etc. I'll just leave it where it is.

Thanks a lot for the info!


-Mike

---

