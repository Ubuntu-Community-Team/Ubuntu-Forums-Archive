---
title: "video on Dell Optiplex GX260"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by winsane on 2007-06-22
I can't get better resolution than 800x600 on my Dell... How do I fix this?

---

### Post by rrinker on 2007-06-28
If you are using the onboard graphics, try going into the BIOS (F2 at startup) and changing the video memory to 8MB. The other option is 1MB. I set ine to 8MB before installing 7.04 and I can run the video all the way up to 1280x1024 (although at only 60Hz).

                             --Randy

---

### Post by SyntaxEscobar on 2007-08-28
> **rrinker said:**
> If you are using the onboard graphics, try going into the BIOS (F2 at startup) and changing the video memory to 8MB. The other option is 1MB. I set ine to 8MB before installing 7.04 and I can run the video all the way up to 1280x1024 (although at only 60Hz).

                             --Randy
OMG, Thankyou.  I ran a search for Dell Optiplex GX260 hoping to solve my issue where startup process froze at a black screen after grub "loaded" the OS.  The 8MB video buffer setting did the trick.  Now it's working fine.

-Mario

---

### Post by JEStoner on 2007-09-09
I had the same issue and all was cleared up with 8mb and updated bios to latest version.  Good luck to all.

---

