---
title: "Partion Icon Lost"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-31
Hi All,

Question: Out of the box my linux install has been able to see my Vista partition.  There was a desktop icon that allowed me to access files, copy to my Ubuntu partion, etc.  Today while I was at work there was a power outage and when the system rebooted the icon is gone.  

I looked for a solution on the forums and saw a suggestion for using "sudo fdisk -l" which i did.  Attached the read-out.  SD1 is my vista part. but where would I find that in filesystem?

Hmm, attachment didnt come up.  

Thanks.

---

### Post by warbread on 2008-01-31
Try looking in /media/sd1 and /dev/sd1.  If it's not in the media folder, then you need to mount the partition again.  If it is in there, you just need to turn the desktop icon back on.

Press ALT + F2 and type in "gconf-editor" without the quotes.  Then go to Apps > Nautilus > Desktop.  Show Desktop Volumes will be an option on the right.

When you do "sudo fdisk -l", just make sure you can see your Vista partition.  If you can't, then that idicates a bigger problem than just desktop icons or mounting.

---

### Post by chewearn on 2008-02-01
Here is what I think happened.

When a partition is automounted, ubuntu create a temporary directory as mount point in /media/
When you have a powerloss, the mount point is left behind.  Thereafter, subsequent attempt to create the mount point again (before mounting) failed.

So, to fix it, look under /media/ and delete the previous mount point.

---

