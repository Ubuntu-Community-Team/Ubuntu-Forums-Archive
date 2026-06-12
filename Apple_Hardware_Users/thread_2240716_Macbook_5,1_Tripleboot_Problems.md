---
title: "Macbook 5,1 Tripleboot Problems"
date: 2014-08-21
forum: Apple Hardware Users
---

### Post by Jeff_Spitzer on 2014-08-21
I am attempting to tripleboot on my Macbook 5,1 (late 2008 unibody Macbook) and it's not going well.  When I first put Ubuntu on my Macbook the tripleboot worked fine.  I had OSX Lion, Windows XP (Bootcamp at the time) and Ubuntu.  Well back in May I lost power while using my XP partition and my ntoskrnl.exe for corrupted.  So after a lot of unceccessful toying around with that I decided to just reinstall Windows.  So I formatted the Windows partition and here where part of my current problem begins.  One of my other problems is that my fantastic CD drive is no longer working correctly.  It just spits out any CD I put into it.  So I can't use my Windows CD to reinstall.  So I created and ISO image out of my install CD (I promise no piracy was done, it's all legit) and I want to know how I can boot from the ISO (whether it's from USB or from the HDD) so I can reinstall Windows?  Also if XP is too complicated, I have access to a Windows 7 install as well.  I just need to make another ISO image.

---

### Post by Dreamer Fithp Apprentice on 2014-08-21
You might want to look at grub-imageboot if you haven't checked it out already. I'm pretty sure there is at least one other program available for booting from an iso on a hard drive but that is the first one I turned up looking in synaptic. If that one won't work try using a search engine with phrases like "booting from iso grub2". Last time I tried booting from isos I found and installed 2 different programs, both in the repo at the time, and one worked and the other didn't, but I don't remember the details and that was a few versions back.

 But even if you get iso-image booting working fine, with this or some other proram, being legal won't gaurantee you can actually boot Windows from an iso in a bare metal real machine. Windows is notorious for thwarting anything the least bit out of the ordinary. If your cd drive can still READ ok, you might get somebody else to burn a disk for you from your legal image.

---

