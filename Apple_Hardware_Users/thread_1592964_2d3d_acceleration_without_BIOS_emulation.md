---
title: "2d/3d acceleration without BIOS emulation?"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by tpievila on 2010-10-11
According to [http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/) BIOS emulation is needed to get 2d/3d acceleration. However on some places (such as [http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/](http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/)) it's claimed that at least nvidia proprietary driver works fine even via direct EFI boot.

What is the current status regarding this? Why would BIOS emulation be needed (I haven't seen a proper explanation anywhere, just "it doesn't work")?

If this would work fine, there would be no longer any reason to use hybrid MBR/GPT approach, if Windows isn't needed.

---

### Post by cath0dez on 2010-10-14
I never noticed that....  bump...  Is rEFIt the reason I am on a never ending video driver quest?

Now that I'm back to my senses and have thought about this one... you don't need to jump through hoops to get acceleration working.  I have rEFIt manager the choice between Linux, Windows, and OS X.  Once I go to Linux grub2 takes over.  The only catch on getting the video drivers going is that I sometimes have to boot into Linux one time with the bootcamp before it works on rEFIt.  After swapping video drivers (or if it just wont load), I usually boot through the ctl/alt menu, go to recovery and boot through the prompt (startx).  Once I'm into the gui I do a terminal shutdown (its usually not available from the start menu in recovery).  Next time I boot rEFIt its good to go and glxinfo is giving me thumbs up on acceleration.

---

### Post by tpievila on 2010-10-14
If you boot from MBR, you are using BIOS emulation of the Apple EFI and there's no difference. If you boot from GPT, the EFI thinks your system is fully EFI capable and most (if not all, that's what I'm asking) video drivers won't work.

Just using rEFIt doesn't really tell which one is the case.

---

