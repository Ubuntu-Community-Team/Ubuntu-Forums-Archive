---
title: "[SOLVED] Partition - Trouble using unallocated space"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by WarmJast on 2007-10-09
Hello there,

I've been using Gutsy/Ubuntu for two weeks now, and am rather enjoying it. I've used up most of the space on the partition I use for Ubuntu, so using the LiveCD & Gparted I've shrunk my XP partition a little but am now having trouble adding the unallocated space to the Ubuntu partition I use.

I've attached a screenshot of my partition manager, and would be grateful if somebody can tell me how I can add that unallocated space to my ext3 partition.

Thanks in advance.

---

### Post by Paqman on 2007-10-09
You'll have to shift your extended and swap partition to the left first. Partitions can't leapfrog over each other.

Have you considered creating a seperate /home partition? Has anybody explained why it would be a good idea yet?

---

### Post by Shazaam on 2007-10-09
sda3 is an extended partition inside which linux resides. You will have to resize (extend) it down to
sda1. The best practice is to reboot after every action before you add another.

1. Move front of sda3 down to sda1. Apply.
2. Reboot.
3. Open gparted to see the results and make another change if you need too. Apply.
4.Reboot.
5.~ ad infinitum.

The unallocated space MAY end up inside sda3, if you need more help come back and ask.

---

### Post by WarmJast on 2007-10-09
Hello Paqman,

Thank you for replying. My swap partition was locked when I booted the LiveCD and tried to move it. Is there something I need to do to unlock it?

I haven't considered a separate home partition, and I'm not sure why that would be a benefit? I'll have a google while I wait for further help with this unallocated space :P

---

### Post by WarmJast on 2007-10-09
Posted at the same time as Shazaam. Thanks, I'll have a try shortly and we'll see how I get on.

---

### Post by Paqman on 2007-10-09
> **WarmJast said:**
> 
I haven't considered a separate home partition, and I'm not sure why that would be a benefit? I'll have a google while I wait for further help with this unallocated space :P

Your /home partition contains all your settings and preferences for your software.

If you reinstall Ubuntu (or any other distro, actually) you can reformat the / partition and leave the /home one intact. All you customisations and settings will be intact. Just like magic!

---

### Post by WarmJast on 2007-10-09
> **Paqman said:**
> Your /home partition contains all your settings and preferences for your software.

If you reinstall Ubuntu (or any other distro, actually) you can reformat the / partition and leave the /home one intact. All you customisations and settings will be intact. Just like magic!

I guess that would be useful, although I'm hoping that I won't have to treat Ubuntu like Windows and re-install every 6 months because it's sluggish and bloated :-) 

I've managed to sort out my unallocated space now by unlocking the swap partition and then moving the unallocated along.

Thanks for your help!

---

### Post by Shazaam on 2007-10-09
Great!

---

