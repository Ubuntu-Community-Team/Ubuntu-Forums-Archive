---
title: "Powerbook G4 12&quot;, Feisty... What am I doing wrong?"
date: 2007-09-28
forum: Apple PPC Users
---

### Post by quadsixmafia on 2007-09-28
Ok, so this is what I've done so far - I can't get past this.  Please help!

So I have an 80GB Internal HD in my PB.  I connected it as a target disk to my Intel iMac, and used "carbon copy cloner" to back up my "Mac HD"  to the imac.  I then used Disk Utility to partition the PB's HD into 5 Partitions - 16MB (HDA1), 1024MB (HDA2), 6020 (HDA3), 6020(HDA4), and the rest (HDA5).

I then used CCC to restore the "Mac HD" to partition 5.  So far, so good.

Then, I restart the powerbook, and boot off of the live cd.  I click install, and proceed to manual partitioning.  I set HDA1 to type "newworld" with mount point /home (it wouldn't let me use / because it say it needed to be formatted, but the box was grayed out).  I set HDA2 to type "swap".  I set HDA3 to type "ext3", with mount point "/".  I set HDA4 to type "fat32" with mount point "/shr".  I leave HDA5 untouched.  

I continue with the installation.  It starts the installation, gets to the Partition part, and then gives me the following error msg:

*The attempt to mount a file system with type swap in IDE1 master, partition #2 (HDA2) at none failed.  You may resume partitioning at the partitioning menu.  *

And that's it... sometimes it'll be HDA1, if I switch the order and make it HDA4, HDA3, HDA2, HDA1, HDA5.  What am I doing wrong?

Thanks!

---

### Post by Doctor J. on 2007-09-28
I have Feisty running on my 12" G4 PB, no probs.  It looks to be an issue with the partitioning.  The <none> in the message you quote doesn't look good.  Unless you absolutely need your partitions in a particular way, you might try the way i did it: 

1) Use Disk Utility, or whatever to make just 2 partitions: the 1st will be Free Space, the other will be for OS X.

2) When you install from the disk, tell Ubuntu to auto partition the free space.  I don't remember exactly what the verbiage is, but you'll see it.  From that point, just let it go.

---

### Post by dynamicv on 2007-09-28
I sorted out the OSX partition first then let the Ubuntu installer automatically partition the remaining space.  In OSX (boot from the install DVD if you've already wiped the drive), partition the drive into two partitions, dragging the bar up or down to get the sizes you want.  **MAKE SURE YOU PUT THE OSX PARTITION FIRST**.  It makes things much easier when you come to install Ubuntu.  Then once OSX is copied back over and you've tested that it's bootable, boot from the Ubuntu Install CD and follow the prompts.

Best of luck.  It's worth it.  And don't forget you can also use Mac-On-Linux to run OSX within Ubuntu once they're both working :)

---

### Post by cheezle on 2007-09-29
I have a question similar to this so I thought I'd post here.

I'm planning to do a Tiger/Xubuntu system on my iMac G5, and I have a few quetstions about the partitioning.

So, I think I'll be resizing the osx partition with the Xubuntu install cd (but first having backed it up) and then I'll use the free space for Xubuntu.


Do I need 3 partitions for Xubuntu (main, swap, and a partition for yaboot)?

Can I re-size the partitions?

---

### Post by idkwot on 2007-10-01
answered my question, thanks guys

---

