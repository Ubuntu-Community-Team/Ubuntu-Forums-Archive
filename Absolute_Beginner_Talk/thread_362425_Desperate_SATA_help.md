---
title: "Desperate SATA help"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Imsati on 2007-02-15
Figured I'd try this Folder as well. I apologize for the cross-post, but every time I boot into Windows, I feel a bit of my soul fade...

I recently purchased a new 80 GB SATA Maxtor HDD. Since then, I've not been able to install Kubuntu by using the Live CD. It always crashes at the Partition stage. It will read both of my SATA hard drives, but will not let me manually partition the one I wish to install to. I was able to successfully install by using the Alternate CD, but after everything was loaded, in order to update the system, I was asked to put in the CD again for some reason, and the file it needed was not available. On a whim, I tried installing Ubuntu and it was fine. I installed the KDE packages from the repositories, but didn't like the end result. I'm looking for a pure Kubuntu install, not simply KDE overlayed on Ubuntu.

I went so far as to download the newest Kubuntu Live CD with the newest kernel, but still no luck. I prefer to use 6.06, but will go to Edgy if necessary.

After some research on both the U/Kubuntu forums, I found some useful information regarding BIOS, but after trying it, still no luck. Any ideas?

Thanks!

Jay

---

### Post by igknighted on 2007-02-15
Your install with the alternate CD is fine, the problem is that the alt. CD leaves itself on the sources.list file.  You need to go in and delete it or comment it out to avoid that message.  As for the Live CD troubles, the only thing I can think is that it must be a bad burn.  Double check you md5 sum on the iso, and try burning it again at 4x speed.

EDIT: I also have an 80gb maxtor SATA drive, and it works fine with no issues installing any linux distro i've tried.  I find it hard to believe that is your problem

---

### Post by Imsati on 2007-02-15
Well, I've used the current Live CD burn to install before so I know it's working fine. That being said, I'm all for thinking outside the box, so I'm burning another at 8x (slowest speed for me) as I post this. If that doesn't work, I'll give the Alt CD another install and uncomment that file afterwards.

I'll post afterwards with my results. Thanks for the quick reply!

Jay

---

