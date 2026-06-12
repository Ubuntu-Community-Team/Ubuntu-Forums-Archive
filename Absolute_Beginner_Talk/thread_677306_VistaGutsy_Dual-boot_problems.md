---
title: "Vista/Gutsy Dual-boot problems"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Penguin_Newbie on 2008-01-24
What guide should I use to set up my Gutsy/Vista dual boot?

The guide I'm using says that Gutsy should recognise Vista before install (where it asks you to confirm settings at the last step before install, mine says Vista should be under the 'Migration Assistant' info?)

But it never is, no matter whether I try to install them on the same drive, or give Gutsy its own drive. 

Any help?  :? 

I'm using this guide:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I'm trying to install 7.10 onto a system with Vista already installed. 

As said, I've tried shrinking Vista's partition (in line with the guide), and I've tried giving Gutsy it's own drive (slave IDE). Vista is on a SATA drive. 

But Gutsy never detects Vista as described. 

I've tried this before, and last time I couldn't get GRUB configured to list Vista as an option to boot into, and then I had massive trouble trying to restore the MBR (which ultimately failed) and was forced to reinstall windows (which was also difficult). 

I'm not keen to repeat that experience and lose all my data again.

My PC is:

AMD Athlon X2 4600+
3072MB DDR RAM
3 HDDs (2 SATA, 250GB (Vista, main drive), 500GB (Storage), 1 IDE (200 GB, slave IDE)
GeForce 7800GTX

Please help! I'd really like to stop being a live session user. :)

---

### Post by Thelasko on 2008-01-25
Ok, In my experience Ubuntu NEVER discovers Visa in the "Migration Assistant."  Your manual says it wont.  I believe I used the same manual you did. Gusty doesn't need it's own drive.  I actually believe it's easier with them both on the same drive.  Just keep going through the installation and everything should work.  I'm assuming you have your Vista installation disk.  You shouldn't have to reinstall Vista if GRUB wipes out your MBR. The Vista install disk has a startup repair tool that will restore it without a complete reinstall.

I've been running a Vista/Gusty dual boot for some time.  Before that it was a Vista/Feisty dual boot. I have never had any problems.  Just always install Vista First! I don't recommend altering GRUB settings if you are a noob.  I believe there are some programs that will guide you through it though.

---

