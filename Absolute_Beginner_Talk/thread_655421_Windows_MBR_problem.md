---
title: "Windows MBR problem"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by the-third-dude on 2008-01-01
Hello. My computer used to be a WinXP/Ubuntu dual boot, but some times earlier I restored the MBR of WinXP using the fixmbr command because I wasn't using Ubuntu much back then so I used this method I found on the net to disable the GRUB menu.

Now I would like to restore the GRUB menu, I find myself don't know how and there isn't so much an answer about this question on anywhere else of the net, so I think I have to ask in here. Do I need to do something to remove the MBR and restore the GRUB menu, and how? Thank you for your attention!

---

### Post by taurus on 2008-01-01
Maybe this is what you are looking for.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by the-third-dude on 2008-01-01
Will the GRUB menu reappear if I simply re-install Ubuntu? My Ubuntu is 6.06 and I just downloaded 7.10.

---

### Post by taurus on 2008-01-01
If you install GRUB to MBR, you should see GRUB menu again when you turn on your computer.

---

### Post by kellemes on 2008-01-01
> **the-third-dude said:**
> Will the GRUB menu reappear if I simply re-install Ubuntu? My Ubuntu is 6.06 and I just downloaded 7.10.


Yes, reinstalling Ubuntu will also reinstall Grub.
But you can also use SuperGrubDisk (see Taurus' link) to fix Grub without having to reinstall your hole system. Could be worth the try..

---

