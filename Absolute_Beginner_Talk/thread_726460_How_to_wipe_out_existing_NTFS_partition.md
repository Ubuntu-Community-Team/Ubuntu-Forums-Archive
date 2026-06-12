---
title: "How to wipe out existing NTFS partition"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Tilex on 2008-03-16
Hi fellow Kubuntu users.

I've used Kubuntu for over 4 years now and I decided to get rid of my NTFS partition where XP is installed; this way, I'll get back a few gigs of hard disk space...

So what I'm trying to do is to format my NTFS partition into a EXT3 partition of the same size.  I've tried using the partition tool in my "System Settings" menu but when I click on my NTFS partition, I can't modify it nor can I simply delete the partition.

I've also tried with gparted.  However, there again, when I click on the NTFS partition, all the options are locked...

Any idea as to how I could re-format my NTFS 25-gig partition into an EXT3 partition of the same size?

Thanks for the help!

Alex.

---

### Post by Oldsoldier2003 on 2008-03-16
> **Tilex said:**
> Hi fellow Kubuntu users.

I've used Kubuntu for over 4 years now and I decided to get rid of my NTFS partition where XP is installed; this way, I'll get back a few gigs of hard disk space...

So what I'm trying to do is to format my NTFS partition into a EXT3 partition of the same size.  I've tried using the partition tool in my "System Settings" menu but when I click on my NTFS partition, I can't modify it nor can I simply delete the partition.

I've also tried with gparted.  However, there again, when I click on the NTFS partition, all the options are locked...

Any idea as to how I could re-format my NTFS 25-gig partition into an EXT3 partition of the same size?

Thanks for the help!

Alex.
you need to unmount the partition or use a liveCD. GParted won't touch a mounted partition.

---

