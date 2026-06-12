---
title: "WinXp not booting after installing ubuntu 5.10"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by vivsmd on 2005-12-21
Hi to everyone. Need help fast! I'm new to linux and dont have that much skill when it comes to computers.  My problem started after resizing and partitioning my hard disk with ubuntu,  my winXP wont boot up and saying some file were corrupted. Dont have problems with booting with ubuntu. Want to keep winXP for now and want to learn ubuntu. What can i do to make winXP bootable again without  reinstalling or deleting somethings.

---

### Post by bscbrit on 2005-12-21
Can you tell me which files are corrupted?  Some can be repaired fairly easily but others will require more serious work!

---

### Post by Synergy6 on 2005-12-21
Well, I don't actually know what file the poster is referring to, but I would hazard a guess at "hal.dll". Not by any scientific reasoning, but because of the simple fact that I have dual-booted many times, with many different distros, and it is the only file which ever buggers up. :)
Synergy6

---

### Post by vivsmd on 2005-12-22
Thank you both for your reply.  The corrupted file is <windows root>\system32\ha1.dll, as mentioned by synergy6. Any suggestions?

---

### Post by bscbrit on 2005-12-22
If you are using XP then I suppose that you are also using NFTS.  Which means that Linux cannot reliably write to it and so you cannot repair the damaged file from within Ubuntu.  If you are using FAT32 then this method of carrying out the repair is still viable.  I do not know how to correct the problem from within Windows XP because I don't use it.

EDIT - Why should the file be corrupted - aren't programs meant to READ DLLs but not try to write to them?

---

### Post by Danielle on 2005-12-22
hi, are you sure it's ha1.dll and not hal.dll? you may be able to fix the hal.dll by editting the BOOT.INI you will need something which can write to NTFS like [ubcd4win](www.ubcd4win.com/) i don't know but maybe if you have your windows cd a repair will fix it too. what is the exact error message?

here's something on the hal.dll error, it's to do with the partitions. i just read the link quickly i think you can use the windows cd
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

---

### Post by vivsmd on 2005-12-23
Sorry about the ha1 , its hal.dll.  thank you for your help. really learning a lot. I'll try your suggestions.

---

