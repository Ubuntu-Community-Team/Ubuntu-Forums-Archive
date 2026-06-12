---
title: "GRUB ERROR 18 - on a modern BIOS?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by jabooth on 2007-01-12
Hey there everyone!

Right situation is this. I have a modern (2 year old max) system A64 3500+, 1gb RAM, 6800gt, etc. Just installed Ubuntu from live CD (6.10 that is) last night and the installation itself was fine and dandy.

Out of fear of destroying my windows data (on a 300gb SATA drive) I chose to install Ubuntu on a separate older 20gb hard drive. This same drive had previously had Vista beta installed.

I completely unplugged the SATA drive leaving only the 20gb drive in. When installing, I chose to erase the entire disk, as I had no more use for Vista. The 20gb HDD is refered to as hdc if thats relevent.

I let GRUB install to default (hd0), which I have picked up is the MBR.

Upon reboot I got GRUB error 18. :-(

So, I tried again, this time specifically partitioning, ensuring the root '/' was at the start of the disk.

No luck!

I also tried using sudo grub and setup (hd0) commands to reinstall GRUB, still get the same problem.

I can't understand what the problem is - Ubuntu is right on the beginning of my drive and I have a modern BIOS - which according to: [http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5)
Suggests I really shouldn't be getting this problem.

Any suggestions?

Thanks a lot, 

J Booth

---

### Post by kebes on 2007-01-12
I agree that you shouldn't be getting "error 18" on a modern BIOS with Ubuntu installed near the beginning of the drive. It doesn't make much sense. It sounds like you've tried reinstalling grub more than once.

I had a "grub error 18" problem once and the only way to fix it was to use LILO instead of grub. You could try installing LILO... I imagine it would solve your current problem. A detailed account of how I installed LILO from a LiveCD can be found in this post:

[http://ubuntuforums.org/showthread.php?t=230384](http://ubuntuforums.org/showthread.php?t=230384)

Hope that helps.

---

### Post by jabooth on 2007-01-13
Sorry, I didn't realise that could have been important - yea I have had grub installed a looong time ago - I thought my reinstalltion would wipe it but - maybe not!

Thanks a lot for the help - I'll try lilo!!

Great forums by the way - I'll really impressed. =D>

J Booth

---

### Post by rumli on 2007-01-16
Can you boot into recovery mode?  If so, after booting into recovery mode, try commenting out the "savedefault" line in the Ubuntu section in the /boot/grub/menu.lst file.

---

### Post by gothrabbit on 2008-02-27
Reactivating this old thread...because I am having similar problems.  (I updated my BIOS so it should be able to handle the 160 GB drive).

One of the posters in this thread says it may occur if you have installed GRUB more than once.  This may be my case, because I tried installing Ubuntu, wiping it and installing Windows, then re-installing Ubuntu.  If I have more than one GRUB install, how can I clean it up?

---

