---
title: "My 3xRAID 0, 1xRAID 1 Setup"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by username132 on 2007-02-09
Aside from my regular data storage drives, I have two of the same SATA drives at 160 GB each. I want to make them into four sections. One NTFS for Windows, and one each ext3 for Ubuntu and Suse all of which should be RAID 0 to make for speed. The fourth and largest section I want to be RAID 1 for information I want not to lose.

Am I right in thinking I should split each drive into four partitons and pair these up to make four volumes (sorry if I'm using the terminology incorrectly)?
How much space should I allocate? I expect something like 5, 5, 5, what's-left (about 135 after file system loses) to give 10, 10, 10, 270 total...

What do people think of my little scheme?

---

### Post by username132 on 2007-02-25
For anyone that reads this in the future (like writing my own little time capsule :) ) I have since determined that my idea is impossible.

RAID works by setting up HDs in a particular way, not individual partitions, so it is not possible to have both RAID 1 and RAID 0 on the same drive. The exception is 'matrix RAID' which is available only on some intel-based motherboards and this does allow RAID 1 and RAID 0 partitions on the same two drives.

---

