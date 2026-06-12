---
title: "Triple boot help"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-04-19
I have three partitions on my system in which I have attempted to install XP, Vista, and Ubuntu. I installed Vista first, then XP, then Gutsy, and I think I may have done those out of order (I think XP should've gone first). The problem is that, initially, only XP showed up in the GRUB menu along with Gutsy. I changed the menu.lst to try and add Vista, but to no avail. I'm thinking what must've happened is that XP overwrote the MBR and made the Vista partition invisible.

XP lives at hd(0,0) and Gutsy lives at hd(0,2). So, in the menu.lst, I tried to point a Vista loader to hd(0,1), but it doesn't go anywhere when I boot.

Do I need to re-install all three, with XP going first this time? Is there a less time-consuming way to fix this?

Thank you!

---

### Post by Oldsoldier2003 on 2008-04-19
> **doctorbighands said:**
> I have three partitions on my system in which I have attempted to install XP, Vista, and Ubuntu. I installed Vista first, then XP, then Gutsy, and I think I may have done those out of order (I think XP should've gone first). The problem is that only XP shows up in the GRUB menu along with Gutsy. I changed the menu.lst to try and add Vista, but to no avail. I'm thinking what must've happened is that XP overwrote the MBR and made the Vista partition invisible.

XP lives at hd(0,0) and Gutsy lives at hd(0,2). So, in the menu.lst, I tried to point a Vista loader to hd(0,1), but it doesn't go anywhere when I boot.

Do I need to re-install all three, with XP going first this time? Is there a less time-consuming way to fix this?

Thank you!

here is a really good tutorial on Multibooting, it should help you sort things out nicely:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by doctorbighands on 2008-04-19
> **Oldsoldier2003 said:**
> here is a really good tutorial on Multibooting, it should help you sort things out nicely:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Yeah, that does look helpful, but it doesn't address my issue. Thanks anyway, though!

---

### Post by bodhi.zazen on 2008-04-19
You do not need to re-install, you just need to configure GRUB.

You need to "hide" the windows installations from each other.

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

You need to know what lives in each partition.

Boot ubuntu and :```
sudo fdisk -l
```

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

