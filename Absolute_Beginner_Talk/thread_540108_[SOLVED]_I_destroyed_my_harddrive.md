---
title: "[SOLVED] I destroyed my harddrive"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by MiniNightMana on 2007-09-01
I put in the live CD and went to the gnome partioner. I created a new partition for the ubuntu install and formatted it to ntfs.
I then went to install. I choose that partition but it said something about a root directory.
So i said to myself...ok Im not smart enough for this and exit out of the install, went back to the gnome partition manager and deleted the partition and put the space back on the orignal one.  Then I restarted the computer.
Now nothing works. Every time it trys to boot up it trys to do the system recovery but gets a fatal error (Im assuming I somehow destroyed that partition) and if I stick the ubuntu CD back in the drive it just locks up..
Do I need to buy a new computer ?

---

### Post by seshomaru samma on 2007-09-01
You don't need a new computer
Boot from the CD again
create a new partition for Ubuntu 
please use [COLOR="Red"]ext3[/COLOR] and not NTFS 
install ubuntu again

before you do that , read more about the procedure [here]("http://www.psychocats.net/ubuntu/installing")

---

### Post by dptxp on 2007-09-01
Ubuntu does not install on NTFS partition, normally you use ext3.
You have to mount the partition as root.
If you delete a partition, you may not see it from any OS, you have to format it.
Windows will see NTFS and FAT32.

---

### Post by Paulmd on 2007-09-01
> **MiniNightMana said:**
> I put in the live CD and went to the gnome partioner. I created a new partition for the ubuntu install and formatted it to ntfs.
I then went to install. I choose that partition but it said something about a root directory.
So i said to myself...ok Im not smart enough for this and exit out of the install, went back to the gnome partition manager and deleted the partition and put the space back on the orignal one.  Then I restarted the computer.
Now nothing works. Every time it trys to boot up it trys to do the system recovery but gets a fatal error (Im assuming I somehow destroyed that partition) and if I stick the ubuntu CD back in the drive it just locks up..
Do I need to buy a new computer ?

You did NOT destroy your hard drive. You so not need to buy a new computer, nor a new hard drive. (Yay!) 

You may have messed up the partitions, rendering the computer non bootable. I won't say 'no big deal' because fixing screwed up partitions isn't all that easy if you want everything back the way it was.

If you don't care about the data, the solution is easy enough. Wipe and reinstall.

That said: hard drives do fail often enough on their own, and a bad hard drive could have caused the partitioner to screw itself up, so it's one thing to check.

---

### Post by Richardky on 2007-09-01
Are you using the live cd ?

if so bootup the cd after it loads just click install and let the default setting do the work for you .

you will be back up and running fast :)

---

### Post by chuckyp on 2007-09-01
Why don't you just boot the xp cd and choose recovery mode and type in fixmbr c: at the command prompt.  Windows will atleast work then.

---

