---
title: "CD-ROM drivers?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by HappyAxolotl on 2006-09-13
I just finished building my new computer. Everything is working perfectly (to my surprise). But I decided to install Ubuntu in the space remaining after Windows XP install. However I am unable to boot off the Ubuntu CD. It boots to the menu and I can choose Boot Ubuntu option. It hangs right after booting the kernel. From what I have read it can be caused by many things. I think my problem is caused by the fact that my motherboard usues ICH8 soutbridge, which does not have support for IDE. And the third-party controller does not accept generic drivers. Gigabyte website has the drivers right here:
[http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=4996&ProductID=2321&ClassValue=Motherboard](http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=4996&ProductID=2321&ClassValue=Motherboard)

So my question is - is there a way to tell Ubuntu which cd-rom drivers I want it to use?

I would buy a SATA drive, but burners are too expensive right now - and there is no drivers for them either at this point. At least I assume that there will be widespread generic driver support for SATA optical drives sooner or later. 

Thank you for your help and please feel free to correct me.
I am new to this forum and Ubuntu, but I really want to learn more about Linux and this distribution in particular.

---

### Post by orb9220 on 2006-09-13
Bootup priority is handled by the bios. If it boots to the ubuntu menu then it is not cdrom driver issue.

If it hangs on bootup it could also be a badlly burned cd. Do not use rw disks and try burning at slower speed.

Otherwise it could be a mobo hardware issue or sata drive issue.

---

### Post by CatKiller on 2006-09-14
> **HappyAxolotl said:**
> So my question is - is there a way to tell Ubuntu which cd-rom drivers I want it to use?

Yes, but I don't know what it is. Never having had exotic drives, I've not had to mess around with these things in any OS install.

If you press F1 (I think - it does say at the bottom) then you can use the F-keys to look at a list of different configuration options that the installer understands. Look for one that seems apropriate and try it out. It'll probably be a command-line-style option that should go in the line that you get from "Advanced" - or whatever it's called in the installer.

Sorry I couldn't be more help.

Edit: Having looked at the Gigabyte page that you linked to, those are DOS drivers. If you wanted to use those, you could get a floppy disk image from bootdisk.com to create a DOS bootable floppy, so that you would have a DOS environment with a working cd-rom drive (once you'd set up Gigabytes drivers, anyway) from which to install Ubuntu. But I think that using Ubuntu's own install environment would be much more preferable, and should be just a case of giving it the right option. But then I know almost nothing about SATA drives.

---

