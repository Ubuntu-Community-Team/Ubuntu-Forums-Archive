---
title: "Did I ruin it?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by big_bad_brad on 2006-09-05
So after hours of ripping cds, I decided I needed more space.  Formatted my second hard drive in xp to NTFS then went to Gparted and set up partitions, 1 with ext2, 1 with NTFS, and another big one with FAT32.  Everything was looking except that I couldn't mount them so I went to Disks, the ext2 partition, and changed the mount point to /home/brad (whoops!).  Is it over?  Did I lose all my info I had been storing? I can't do anything.  Please help.

---

### Post by monktbd on 2006-09-05
no... just unmount it again from /home/brad and your old home folder will appear (if it wasnt on a different partition before).
if it was on a different partition before you need to mount this partition as /home/brad.

remount the new partition into a subfolder of /home/brad to use it within your home folder.

---

### Post by steve.horsley on 2006-09-05
As monktbd says, just unmount /home/brad again. Assuming you can get sudo to work - if not, you need to reboot.

Remember that mounting a partition just hides the original content of the mount-point folder. The original stuff is still there, just not visible while the other partition is mounted there.

---

### Post by whizbaby on 2006-09-05
Actually it's NOT as easy as that to delete information off a hard disc (some companies can recover data of burned, drowned or fallen-out-of-the-window HDs), you have to use special tools for that (e.g. shred). So:
Don't Panic!

---

### Post by big_bad_brad on 2006-09-05
Maybe I jumped the gun. When I first did this my whole desktop crashed and I thought oh no.  Then I went to the live cd and saw nothing I wanted to see, and couldn't do anything.  Next went to xp and typed the above thread, read your responses (Thank you) and restarted ubuntu.  Everything was back the way I wanted it.  I don't know what happened.  But where is the best place for the access points of my second drive partitions?  Partition 1 is the NTFS partition and 2 and 3 have no access points and are labeled inaccessible.

---

