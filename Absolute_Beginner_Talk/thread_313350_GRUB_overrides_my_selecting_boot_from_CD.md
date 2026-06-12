---
title: "GRUB overrides my selecting boot from CD"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by fez on 2006-12-05
I have had quite a few problems with Ubuntu, mainly to do with wireless cards. Had an unsupported one which I couldn't get to work even with NDISwrapper. Finally bought a new, supported one and it was recognised, but now I can't boot into Ubuntu.

The boot stalls on Network Devices (or whatever the correct term is), and I have to ALT+C to get past it. Then I'm faced with the log in screen. I log in and then the screen goes light blue (I think it's the loading screen for Gnome) but the windows server and nautilous etc. do no load. It just hangs.

I've downloaded Edgy so that I can reinstall (after trying many things to get my current install working, although I don't really know what I'm doing). I set my BIOS to boot from CD but GRUB seems to override it somehow and I only get the option of XP or the broken Dapper.

Have tried lots of other bootable disks, including floppys, but GRUB overrides them all.

What can I do? Is there a way to install Edgy without it booting from CD? I can load KDE but hardly anything works. I eventually got a different file manager to Konqueror (which doesn't load) working so that I could browse the CD, but I don't know how to install that way.

Sorry for the long post! ](*,)

---

### Post by kakalaky on 2006-12-05
If you are making it to grub either the cd is not bootable, your cd drive has issues, or it's not trying to boot from the disk.  I would start with checking your bios again just to make sure you have the correct boot order.

---

### Post by fez on 2006-12-05
I have checked, checked, and rechecked it many times over the last few hours. I had wondered if it was a problem with the drive. In BIOS it only gives me the option of CD, but it's a DVD/CD drive. Should this be a problem?

---

### Post by kakalaky on 2006-12-05
Boot into win and make sure the drive is working properly.  If it is working properly there the problem is most likely with the disc itself.  Check your download against the md5.  If they match, try burning the disc again at 4x.

---

### Post by fez on 2006-12-05
The drive is fine. How do I check the md5 (in windows?). If it's a case of burning the disk again, I'll have to call it a night soon. Getting a bit late here!

---

### Post by kakalaky on 2006-12-05
You can get a program to check the md5 here:

[http://sourceforge.net/projects/md5summer/]("http://sourceforge.net/projects/md5summer/")

---

### Post by fez on 2006-12-05
Thanks a lot for your help. Just going to check it now.

---

### Post by fez on 2006-12-05
Hmmm. I can only find md5sums for Dapper. Where would one find them for Edgy?

---

### Post by kakalaky on 2006-12-05
[ftp://mirror.d-jacobs.com/ubuntu/edgy/MD5SUMS]("ftp://mirror.d-jacobs.com/ubuntu/edgy/MD5SUMS")

---

### Post by fez on 2006-12-06
Thanks for your help. I did what you suggested and it installed fine. I still can't get the wireless connection working. I'm almost at the stage of giving up. ](*,)

---

### Post by fez on 2006-12-06
It seems my card doesn't work with Edgy (rt2500). How amusing! My last card didn't work with Linux full stop (am1772). Is there an easy way to fix this? Would I be best just going back to Dapper, where apparently it did work? (Is rolling back to an earlier version easy?)

---

