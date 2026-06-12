---
title: "Replace 2nd hard drive?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by RetroFreak on 2007-08-12
I have two 40gig hd's in my system (running Feisty). The 2nd one has /home and swap partitions, everything else is on the 1st hd.

I want to replace the 2nd drive with a 120gig. Can I do this easily without reinstalling? If so what's the best way? Fit the 120 first and set it up, or unplug the old drive and fit the new one?

I can do a complete re-install if needed, but seems a bit of an effort just to replace a second drive.

TIA

---

### Post by chewearn on 2007-08-12
Here is how I would do this:

a) Plug in the 120GB HD
b) Partition it, including create a new swap
c) Copy the files over for /home (make sure its all files, including hidden ones)
d) Backup fstab; edit fstab to point to the new drive (use UUID, instead of hdxx; so that the references are not absolute)
e) Shut down, unplug 2nd 40GB HD
f) Boot up; see if all is OK

If not OK, you can restore the fstab, put back the old 40GB HD, and everything should be back to previous state.

---

### Post by ridgeland on 2007-08-12
I would squeeze enough space out of drive1 to hold a small version of /home, just the essentials and a small swap like 512MB.  Then edit /etc/fstab to point /home to drive1 rather than drive2, also swap to drive1.  Verify it boots and runs OK.  Check with $ free. (Oh course if /home is full of /home/movies, /home/images... they will stay behind on the old drive for now.)
Then replace drive2.  Put a /home on the new drive2 and more as needed.
Then copy everything you can from drive1 to the new drive2 and make lots of space on drive1.  Then put the old drive2 back in and copy all you can to the newly freed space on drive1.  Then swap drive 2 again and copy the new stuff from drive1 to drive2.  The repeat swapping drive2 and walking data across via space in drive1.  The more data the more swaps, the less space freed up on drive1 the more swaps.

I use cp -a to copy partitions.  Study it with $ man cp

Must be hundreds of ways to approach the challenge though.

Since you're booting from drive1 just making a new /home and swap there should mean you don't need to reinstall.

---

### Post by RetroFreak on 2007-08-12
Ta for the suggestions :)

I should mention that everything on the 2nd HD is backed up, so no worries there. I'm about to go and play :)

---

