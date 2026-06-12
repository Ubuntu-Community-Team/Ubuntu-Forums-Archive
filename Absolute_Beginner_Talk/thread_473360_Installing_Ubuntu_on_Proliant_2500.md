---
title: "Installing Ubuntu on Proliant 2500"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by RMWChaos on 2007-06-14
This is not my first install of Linux on this little beasty, but it is proving to be the most challenging.

In the past while installing one version of Linux or another I learned that these Proliant 2500s do not accurately report the amount of memory to Linux...it only reports the first 15MB unless you modify the LILO boot command to include the lines
   
    linux mem=exactmap
    mem=xxx@xxx
    mem=...

And there are some more recent (more complicated) hex-based methods of doing it as well that I believe were posed in these forums somewhere.

The problem is, I can't do this to the installation CD, and my installation bombs out. So my thought is to boot to a floppy where I set mem=... and then initiate the installation on the CD.

Anyone have any thoughts on this? Is there a way to modify the ISO image before I burn it to the CD so that it automatically sets the memory before installation?

Thanks.

---

