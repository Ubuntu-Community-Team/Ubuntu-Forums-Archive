---
title: "[SOLVED] How choose among OS in the same computer"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by hquijanog on 2007-12-30
Hi!, some months ago I had Windows XP. Then I created a new partition and installed Ubuntu on that partition. Everything worked fine, every time I turned on the computer, it showed a menu where I could select which Operative System I wanted to load.

Nevertheless, a week ago I decided that my Windows partition needed to be formated and installed again (a common windows users practice). So I formated only the Windows partition and then installed Windows XP on it. I got a very big surprise  when next time I tunrned on the computer, it didn't showed the menu where I could select which Operative System I wanted to load. Instead of that, the computer loads Windows XP.

The Ubuntu partition is still intacts, but I don't have access to it. My big question is what I need to do with my windows partition to be able to see the select Operative System screen again. I don't want to reinstall Ubuntu because I have many important files there. Besides, I don't want to configure Ubuntu again.

Thanks in advance for all the support you could give me.

---

### Post by doorknob60 on 2007-12-30
Windows overwrited the GRUB boot loader, so you need to reinstall GRUB. I think there is something called Super Grub DIsk which is a bootable CD that can do this for you. I've never used it though, just Google it and you should find it.

---

### Post by hquijanog on 2007-12-31
Thank you!, I just used the Super Grup Disk and it fixed my problem. Now I can see the screen with the OS selection again.

Thanks a lot.

---

### Post by doorknob60 on 2007-12-31
Glad to help :)

---

### Post by mrdak on 2008-01-01
> **hquijanog said:**
> Thank you!, I just used the Super Grup Disk and it fixed my problem. Now I can see the screen with the OS selection again.

Thanks a lot.



The same thing happened to me :(  I have XP and Gutsy on separate partitions..... separate drives actually.  

Could you please post the exact choices you made from the Super Grub Disk? I would so much appreciate it. 

Thanks

---

