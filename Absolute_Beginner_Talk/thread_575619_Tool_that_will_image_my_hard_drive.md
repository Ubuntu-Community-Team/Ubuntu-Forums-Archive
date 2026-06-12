---
title: "Tool that will image my hard drive?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-10-14
Hey!
 
I am in the process of getting my computer back in order. Whenever I have to do this, I have to install windows, install drivers, install Safari, install office, install photoshop, etc; 
 
I was wondering if there was a way I could somehow copy this perfectly configured windows over to a DVD or CD so that the next time I screw up my computer, I just pop in the DVD and copy the image over to the Hard Drive. 
 
I don't need to do this for Ubuntu since it works perfectly from the start. 
 
If anyone knows how to do this (for free... that's why I use linux) could you please post and tell me how?
 
BTW: I know I could use Windows' SYstem Restore But I am not interested in doing so. 
 
Thanks, 
 
TIm

---

### Post by steve.horsley on 2007-10-14
There is a product called partimage that runs on Linux, but its NTFS support is said to be "experimantal" at the moment. 

The *nix way would be to use dd but it creates an image that is the same size as the partition you are imaging - it is a bit-for-bit copy of the partition. If you have the backup capacity, this is the way I would suggest, but clearly, a DVD won't be enough. You may be able to compress it with gzip of course.

---

