---
title: "Found a strange fix (?) to ntfs drives not showing up"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by skippy_dude on 2007-10-22
I just did a fresh install of Kubuntu 7.10 and saw that although it had detected my fat32 drives it had missed my ntfs drives. One of which is a logical extension of a main drive and one separate huge drive.
So got gparted to take a look at the partitions and saw that ominous exclamation mark beside my (logical extension) ntfs partition there. Dunno if it even saw my other drive at that point.
I booted into windows and ran chkdsk on both drives, I even cancelled the chkdsk at the stage 4 or 5 where it starts to get slow always and ran a full chkdsk on the logical extension drive.
Now booting into kubuntu I see the large drive (on which chkdsk was cancelled) is showing up and automounting but the other one still is not.
Again boot into windows and see if the drive needs defragmenting, it does. The larger drive did not. So I defrag and boot into kubuntu.
Now suddenly both drives appear and automount!

Could someone explain why this worked?

Note: Just after I installed Kubuntu the first thing I did was start booting into windows to see if I could, at that point of XP where it shows the green loading bar on a black screen, I hit the reset button and I think that's where the issue started.
I'm also not eager to try to reproduce the problem by resetting in the middle of windows....

---

### Post by Paqman on 2007-10-22
I don't know about the defrag, but I know that my NTFS partition won't mount if has flag on it saying that it wasn't shut down properly. Usually this is due to Windows being spastic. A simple boot up and correct shut down of Win sets the flag to "clear" and the partition mounts automatically in Linux.

---

### Post by lonesomecrow on 2007-10-22
> **Paqman said:**
> I don't know about the defrag, but I know that my NTFS partition won't mount if has flag on it saying that it wasn't shut down properly. Usually this is due to Windows being spastic. A simple boot up and correct shut down of Win sets the flag to "clear" and the partition mounts automatically in Linux.
that is what I figured, cuz my friends computer is down so I wanted to see if the hard drive was bad so I plugged it into one of my SATA spare connection and it told me something about an improper shutdown, I had to force-mount it tho of course!

---

