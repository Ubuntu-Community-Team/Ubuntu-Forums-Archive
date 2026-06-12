---
title: "Update to Mountain Lion"
date: 2012-08-26
forum: Apple Hardware Users
---

### Post by eivindsm on 2012-08-26
Hi guys, what are you experience updating OSX to Mountain Lion for dual booted setups? I've got a dual booted iMac with 12.04 and osx 10.6. I went thru quite some pain to get it up running, and I wonder if ML is worth the hazzle. 

Cheers!

---

### Post by entangled on 2012-08-27
I had triple booting OSX 10.7, ubuntu 12.10 and archlinux on a pure gpt disk. rEFInd was installed on OSX. Linux boots used efistub only (no bootloader, like grub2 etc).
This setup would not allow ML to install over Lion - just told me my main disk is not available! 
After abortively experimenting with adding unused gaps between partitions, I finally backed up Lion to external drive, reformatted just the Lion partition, using Disk Utility from Lion boot DVD, then installed ML in the newly reformatted partition.
Re-installed rEFInd in OSX 10.8 (just copy a folder and do a bless command) and carried on with linux as before. The EFI partition (first on my disk) holding the linux kernels for booting via rEFInd, was not touched by the OSX update. 
As far as I can see ML is much the same as Lion, but at least it gets latest updates.

---

