---
title: "Recover seperate backed up partitions to one partition"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2006-09-16
Because of hard drive constraints and running out of space in some partitions, I decided to redo my whole partitioning.

This is what I did.
I used Acronis to back up my partitions on a spare hard disk.
I had the following mount points for my partitions. /usr  /var  /home  /swap and of course the root.
The problem was the spare disk had a lot of data, so I had to shrink the partitions so it can all fit on one drive.

Next I re-installed Kubuntu on the new disk, but with only a large root and a small swap partition. Now I can see me old files and set-up sitting in the back-up partitions on the spare drive, with no apperant data loss.

Now the bit that I don't understand, is how do I get my original set-up working in the new single partition? 

I found this write up.> Re: Repairing the ubuntu 

--------------------------------------------------------------------------------

Good news is your data should all be there. The bad news is that it is now hidden. What I would suggest is that you boot up using a live CD. Mount the current / filesystem mkdir /newhome. Then vi or edit the /etc/fstab and point your new partiton to /newhome. Then reboot and you should be back to your starting point. You can then copy (cp /home/* /newhome - Rf) your /home directories to your /newhome. Then umount /newhome and change /etc/fstab to mount /newhome back to /home. Note that doing this will leave your old home folder alone, but hidden so there is some wasted space on your / filesystem. When everything runs OK you can boot up in the live cd again and delete the old stuff (being careful of course to only mount the old / file system and not the new one). Hope that made sense.

This is not very clear for me, although the general outline is clear, this seems to me that you effectively rename your old partition(s) to whatever the new ones should be. I want the old data in the new one! Simply copying the data from one partition to another seems like a bad idea.

Any suggestions as to the easiest working method?

---

### Post by GrootBrak on 2006-09-17
Boinnnnngggg.:biggrin:

---

