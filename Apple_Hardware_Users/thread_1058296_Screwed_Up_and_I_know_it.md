---
title: "Screwed Up and I know it"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by DavidFromCanada on 2009-02-02
Okay I love Ubuntu so I was trying to put it on a memory stick to boot on my Eee PC. So I put the disc in my iMac and properly managed an installation onto my memory stick. Well when the process got to installing GRUB I realized my mistake. I realized that grub was overriding the Mac OS X bootloader. So I turned the computer off and restarted (to hell with the installation) and realized how the computer didn't see my Macintosh HD. So I pulled out my Mac OS X install disc and booted it up. I repaired the Hard Drive and tried to boot up into the Hard Drive with the Startup Disk utility. No luck, so now I'm trying an archive and restore installation of Mac OS X. Worst case scenario that it doesn't work, where should I go from there?

---

### Post by mkvnmtr on 2009-02-02
I don{t know if there is a better way for you but what I would do on my mac is boot the Ubuntu disk. Then I would go into th mac os to extract my music files or any thing else I thought I could need. Then I would reinstall the Mac os. The problem is if you have apps you have paid for and don{t have the installers backed up. I always save the things I installed on an external hard drive but you may not have. I suppose you could just copy the whole os to an external drive and then file by file put your stuff back when you reinstall. That is how I put the configuration back in my home file for the few things that are inportant when I reinstall Ubuntu.

---

### Post by cyberdork33 on 2009-02-02
> **DavidFromCanada said:**
> Okay I love Ubuntu so I was trying to put it on a memory stick to boot on my Eee PC. So I put the disc in my iMac and properly managed an installation onto my memory stick. Well when the process got to installing GRUB I realized my mistake. I realized that grub was overriding the Mac OS X bootloader. So I turned the computer off and restarted (to hell with the installation) and realized how the computer didn't see my Macintosh HD. So I pulled out my Mac OS X install disc and booted it up. I repaired the Hard Drive and tried to boot up into the Hard Drive with the Startup Disk utility. No luck, so now I'm trying an archive and restore installation of Mac OS X. Worst case scenario that it doesn't work, where should I go from there?
boot the Ubuntu CD

install refit (sudo apt-get install refit)

sync the partition tables (sudo gptsync) 

then reboot.

OS X doesn't have a bootloader like that, so I don't think you "overwrote" it.

If you are reinstalling, then that will probably fix it anyway.

---

### Post by DavidFromCanada on 2009-02-03
Okay solved it. I downloading rEFIt and burned a disc. Then I repaired the EFI tables on the disc. Then things worked again.

---

### Post by DavidFromCanada on 2009-02-03
Ah where is the mark as solved button? Its not in the thread tools!

---

### Post by pxwpxw on 2009-02-03
its in the Thread Tools at the top.

---

### Post by DavidFromCanada on 2009-02-03
I know it's supposed to be there but it isn't!

---

### Post by pxwpxw on 2009-02-03
> **DavidFromCanada said:**
> I know it's supposed to be there but it isn't!

Yes just checked on my threads - wonder where it went?

---

### Post by Neural oD on 2009-02-03
the solved feature has been temporarily suspended - for now

---

### Post by DavidFromCanada on 2009-02-03
> **Neural oD said:**
> the solved feature has been temporarily suspended - for now
Without the solve button how will things be solved on the forum?
*Ubuntu Forum Implodes*

---

### Post by Neural oD on 2009-02-03
Well the servers were taking strain - so the admins decided to get rid of things that were causing some unneccessary overhead.

---

