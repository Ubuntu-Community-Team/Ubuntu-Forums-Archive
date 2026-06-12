---
title: "Need to go back to Vista, forgot to partition hard disk"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Edd11111 on 2008-02-19
First of all, I love Ubuntu. But I need to go back to Vista for some products. But I forgot to partition the Hard disk. Is their any way to partition the disk (for both formats) now?

---

### Post by Het Irv on 2008-02-19
Pop in your Live-CD and use the Partition Manager to make a NTFS partition, for Vista I think you need to have at least 20Gigs.  Depending on the size of your drive 30 or 40 would be best.  
If I remember right Partition Manager is under System -> Administration

---

### Post by SunnyRabbiera on 2008-02-19
well what was it on vista do you need?

---

### Post by imT on 2008-02-19
> **Edd11111 said:**
> I need to go back to Vista

:lolflag: if you would said u have to go back to xp i would understand in a way, but vista ? :lolflag:

---

### Post by Edd11111 on 2008-02-19
Every time I try to put in my CD and restart, it just goes straight to Ubuntu, it doesn't say "Press any Key to boot from disk" like it would do normally.

---

### Post by Fred_E _krugar on 2008-02-19
Thats because you dont have Boot from CD first in the BIOS.

---

### Post by Het Irv on 2008-02-19
Is your BIOS set up to boot from CD?   Also it should pop up with a menu automatically, only windows disks come up with "Press any key to boot from disk"

---

### Post by Edd11111 on 2008-02-19
Yes, but it still is not working. This is strange, because I did what I did before to install Ubuntu, and now it is not working. Could it be my CD? Or am I just missing something?

---

### Post by Het Irv on 2008-02-19
Are you using the same CD that you used to install?  Also check to make sure that your CD is working, just in case.

---

### Post by Edd11111 on 2008-02-19
I did put the CD in my computer, it came up like any other normal data CD, with all the files viewable. This might not be the same disk I used to install with. I burned a few disks, and I think I gave the disk that I installed this with to my friend. It was a Feisty Fawn disk, and I upgraded to Gusty Gibbon via update manager, if that helps.

---

### Post by Het Irv on 2008-02-19
Did you burn the CD as an .iso?  If you can try burning another just to make sure.  If the CD is not an .iso it will not boot.

---

### Post by tekguy on 2008-02-19
Does your system have a boot menu? Some bioses actually have a boot menu that you can bring up to specify what device to boot from.

---

### Post by Edd11111 on 2008-02-19
Ok. Thanks for all you help, Het Irv, now I get this message from the windows installer: "Windows is unable to find a system volume that meets its criteria for installation". Can you help with this error in any way?

---

### Post by seventhc on 2008-02-19
you'll need to boot from the live cd and use gparted to create a partition that windows can recognize. If it's all ext3 and a swap, I think windows won't know what to do. so create a partition, format it in NTFS. Then boot back to the windows CD.

---

### Post by Edd11111 on 2008-02-19
Thank you, everyone who helped me. I downloaded an installation disk of Ubuntu 7.10 and used the Partition editor to split my hard drive into two seperate formats. The only thing I missed was checking the "boot" box in the partition editor. Now I dual-boot Vista and Ubuntu!

...And for some reason, this does not feel like it is such a great thing :p .

---

### Post by Het Irv on 2008-02-19
Mark the thread as solved so that other people will know that this thread has a solution.  Also I wouldn't mind if you click the Thanks button on one of my posts, its the ribbon button next to quote.

---

