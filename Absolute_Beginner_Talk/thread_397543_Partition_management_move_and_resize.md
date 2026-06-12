---
title: "Partition management: move and resize"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by grEnAlEins on 2007-03-30
I am looking to move and resize my Ubuntu Partition.  I made a small partition at first, only a couple gigs.  I want it to be bigger.  I resized my Vista partition (shrunk it by ~25gig)  I want to add said ~25gig to my Ubuntu partition.  The unallocated space that I wish to add comes before my Ubuntu partition.  I made a live cd of gparted.  Before I move or resize anything I want to make a full backup because I had to wrestle with ndiswrapper/my wireless card to get it to work, and had problems with a few other things, not to mention stuff I have saved.  I found some directions:

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

Are the files he is saying to exclude important?  Why are they excluded?  If I want to make a complete backup so that I can just restore and not have to do anything else, what should/shouldn't I exclude?  I know to exclude the backup file itself and my Vista partition.  If I burn the backup file onto a cd with the other partition excluded, when I restore will it still know to mount that partition? (I am using "--exclude media --exclude mnt --exclude backup.tgz" as the exclusions)

I also recall hearing that I can use the dd command to make an exact copt to a DVD.  How would I go about doing this?  I only have ~3gig of stuff in the file system as of now, but I am gonna start using Ubuntu as my primary OS, so I will need more space.  The partiton I have now is roughly 5.25gigs, but 2.5 is empty.  If I use dd, will I be able to use only one DVD (4.7gig)?  I only have ~3gig of data, so I would think so, but the whole partition is over 5gig, so that leaves doubt in my mind.

It has crossed my mind that I could copy my Ubunutu partition to the unallocated space to make a new 25gig Ubuntu partition.  I could then delete the old one, and add the space to the new partition.  Would that be faster/easier/safer/better?  It would work, right?

Thanks in advance fo your time and assistance,

Nick

---

### Post by jerryrw on 2007-03-30
Yes those files should be excluded.  /proc and /sys are dynamic 'filesystems' that basically contain info about running processes.

You SHOULD be able to just do a copy to the larger drive and only have to change your boot loader config and your /etc/fstab.  Just make sure that the directory tree is EXACTLY the same.  You should be able to test this and leave your existing system alone buy formating the new fs on the new drive doing the copy then adding the new boot entry to grub (not removing the old one).

---

