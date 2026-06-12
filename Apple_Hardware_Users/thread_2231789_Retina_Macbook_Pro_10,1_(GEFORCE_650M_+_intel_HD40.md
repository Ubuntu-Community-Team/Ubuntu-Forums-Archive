---
title: "Retina Macbook Pro 10,1 (GEFORCE 650M + intel HD4000) graphics switching on 14.04"
date: 2014-06-27
forum: Apple Hardware Users
---

### Post by llamaswill on 2014-06-27
Hey! I'm (like two minutes) new to being on the Ubuntu forums, but I have a decent bit of Ubuntu knowledge.

I have a mid-2012 retina macbook pro and it has two graphics cards... one of them is a high-performance NVIDIA 650M and the other an intel HD4000. In OS X, only the HD4000 is active; it can be forced to run using gfxCardStatus for Mac and certain apps (like games) activate it.

In Ubuntu, I can only get &#8776;2 hrs. battery life since only the NVIDIA card will run. I've seen some other forums on this and tried every single suggestion; they no longer work with 14.04 and the SMC firmware upgrade.

Has anyone had success getting 14.04 and the HD4000 to coexist? As of the latest version intel graphics installer does run but I can't get it to switch to the integrated card :(

On OS X going integrated-only shoots battery life above 8hrs with browsing or reading. If I could get that on Ubuntu, I would switch to it as a primary OS!



I've got a pretty complex multi-boot system; here's the output of diskutil list in OS X:

```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *751.3 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                  Apple_HFS Mac SSD                 423.2 GB   disk0s2
   3:                  Apple_HFS Yosemite                63.3 GB    disk0s3
   4:       Microsoft Basic Data BOOTCAMP                180.1 GB   disk0s4
   5:       Microsoft Basic Data                         48.0 GB    disk0s5
   6:                 Linux Swap                         16.1 GB    disk0s6
   7:       Microsoft Basic Data SHARE                   4.0 GB     disk0s7
   8:                  Apple_HFS Mac Recovery            14.6 GB    disk0s8
   9:                 Apple_Boot Recovery HD             650.0 MB   disk0s9

```

disk0s0 is GPT (with hybrid MBR set up for BOOTCAMP), s1 is EFI, s2 is my primary OS X partition (with rEFInd installed as a boot picker), s3 is the OS X 10.10 beta, s4 is BOOTCAMP, s5 is Ubuntu 14.04, s6 is swap for Ubuntu, s7 is a shared storage FAT partition, s8 is another OS X partition for repairs and so I can have an OS X recovery partition (they have to immediately follow an OS X partition), and s9 is that recovery partition.

---

### Post by MikeBraxner on 2014-06-28
14.04 on a mid-2012 MBPr 10.1 ... using ***only*** the i915 works without a hitch, appr. 7 hrs on battery with a few tweaks. As for the install, I basically used the routines worked out back in 2012 (gfxCardStatus, vgaswitcheroo, ...). 

If you're getting ~2 hours on the NVidia, then either something is seriously wrong with your install, or you're pushing your graphics *hard* ... last I tried, I got about 4.5 hours without much effort.

I would suggest to take another look at, say, [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) for the basics, [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304) on how to handle the NVidia, and [http://cberner.com/](http://cberner.com/) for a primer on a working installation, including Thewho's comment on *'disabling “quiet” and “splash” in the GRUB-config'.* You might also want to re-read some of the 'old' stuff, e.g. the comments on 'double-rebooting' to get a gfxcardstatus forced switching to 'stick' for a boot into linux ... just a thought ;-)

---

### Post by llamaswill on 2014-06-28
Did you ever install the SMC update for RMBP?

---

### Post by llamaswill on 2014-06-28
Also, did you get the Mac or non-Mac ISO? I've been told to use (and had more success with) the non-Mac, but [http://cberner.com/2014/04/20/installing-ubuntu-14-04-on-macbook-pro-retina/](http://cberner.com/2014/04/20/installing-ubuntu-14-04-on-macbook-pro-retina/) links to [http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/](http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/) which says to use the Mac ISO in step 3...

---

### Post by MikeBraxner on 2014-06-28
***SMC Update*** ... yep

***Mac or non-Mac ISO*** ... I used the Mac version for two reasons: (i) I had used mac versions for all previous installs on MBPr, i.e. my notes and procedures are based on them (*if it ain't broke ...*), and (ii) the only 'real' difference is the necessary correction to proper EFI-boot.

---

### Post by llamaswill on 2014-06-29
Hey, I've done some more research and trials and got it to work!!! :)

Relevant tips:

1. GET THE NON-MAC ISO... I did some more research into it, and it's better in every single way.
2. Get the right version of gfxCardStatus (I've uploaded one for anyone that wants it - it's at [http://cl.ly/1G1i431W1Q2d](http://cl.ly/1G1i431W1Q2d))
3. Format a thumb drive then use unetbootin to make the thumb drive (if it doesn't work google "ubuntu thumb drive install mac" and follow the instructions)
5. Make another OS X partition at the end of your disk if you want an OS X recovery partition (they can only be immediately after an OS X partition)
6. Install GRUB (using standard install, and onto the same partition as Ubuntu) and rEFInd, and boot the EFI version of GRUB using rEFInd
7. Boot into OS X after installing Ubuntu and use gfxCardStatus to switch to your integrated card, then reboot into Ubuntu and run Intel Linux Graphics installer - that's all it really took for me to get integrated graphics :)
8. Battery life is still okay at best - 4hrs or so. I'm working on some (not-yet-stable) tweaks that get it up to 8hrs with lower battery life
9. If you want BootCamp / Windows installed, it's much more complex... if anyone is interested please tell me and I'll add detailed instructions + screenshots!


Anyone got some more battery optimization tips? I'll post more as I find the most stable versions!

---

### Post by llamaswill on 2014-06-30
Also, has anyone got optimus / bumblebee working?

---

### Post by MikeBraxner on 2014-07-02
Since Apple decided to use its own switching design, i.e. non-optimus, bumblebee can't work, so no flexible runtime switching between GPUs.

---

