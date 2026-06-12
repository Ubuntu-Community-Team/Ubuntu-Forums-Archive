---
title: "Problem with 7.10 alternate install to laptop"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Jittoku on 2007-11-11
Can anyone help me with this?  I'm just learning about Ubuntu, and I've got my desktop working fine, but . . . 

I have a 2 yr old laptop (from Linux Certified, model LC 2210DE, 1 Gb, some kind of Intel chip, I think) that I was running Fedora Core 3 on for 2 years with no problems.  Over the last week, I've been experimenting on it with Ubuntu. 

I was able to load Feisty from the live CD, no problems whatsoever, and ran great.  I let it repartition.  Then, just out of curiosity, I tried loading Fluxbuntu, for no particular reason.  I tried a clean install, letting it repartition as it wanted to.  (Fluxbuntu was a text based installer.)  The installation stalled with a message about being unable to install the base system - 

"Target file system contains files from a past installation.  These files could cause problems with the installation process, and if you proceed, some of the existing files could be overwritten.  Proceed with installation to unclean target?"

I was never able to get past this problem.  I wasn't really that into Fluxbuntu, so I just left it, and went ahead and installed Gutsy from the live CD.  Again, as with Feisty, no problems, perfectly smooth, and everything ran great.  

Then I was reading about installing to a fully encrypted disk, which I wanted for the laptop, so burned the 7.10 alternate ISO and tried installing from that.  Darned if I didn't get the exact same problem as with the Fluxbuntu install, with the exact same message as quoted above.  It seemed to have problems with the kernel, and asked me to choose from a list of four - generic, image-generic, something else, and "none".  Tried the first two, but it always hung up somewhere over the next few steps.  I don't know why to choose one over another, anyway. 

Of course I did a checksum on both disks.  I did run the disk check on the failed 7.10 alternate, and it found an MD5 checksum problem somewhere.  Never checked the Fluxbuntu disk that way.  But could it really be the disk?  What are the odds that both of those disks that I tried the text install from were corrupt, when the two GUI installs went fine?  

Thanks in advance for any help you can give!

---

