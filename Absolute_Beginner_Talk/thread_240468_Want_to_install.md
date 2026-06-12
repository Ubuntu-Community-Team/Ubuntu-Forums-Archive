---
title: "Want to install"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by edman2 on 2006-08-20
Okay so I've cleared off 20gigs off of one of my non-boot hard drives (G: ) that I just use for storage and I want to install Ubuntu on it. I don't want to install on my Winxp boot C, or D because they are both on a Raid-0 array I have set up and I don't want any complications. I plan on just choosing what I boot to by changing my boot drive in the bios whenver I feel like using the OS I want. This should work fine right? I don't have to install on C or D?

Also, I've defragged the G drive after I cleared off the space, anything else I should do? To be honest my only real concern in all of this is #1) my raid disks getting messed up somehow, which would mean loss of A LOT of stuff, or #2) my G drive getting messed up which would also result in a lot of stuff...

---

### Post by nalmeth on 2006-08-20
> **edman2 said:**
> Okay so I've cleared off 20gigs off of one of my non-boot hard drives (G: ) that I just use for storage and I want to install Ubuntu on it. I don't want to install on my Winxp boot C, or D because they are both on a Raid-0 array I have set up and I don't want any complications. I plan on just choosing what I boot to by changing my boot drive in the bios whenver I feel like using the OS I want. This should work fine right? I don't have to install on C or D?

Also, I've defragged the G drive after I cleared off the space, anything else I should do? To be honest my only real concern in all of this is #1) my raid disks getting messed up somehow, which would mean loss of A LOT of stuff, or #2) my G drive getting messed up which would also result in a lot of stuff...
If you're really worried, you should backup any valuable data. If you know what you're doing with BIOS booting, then use the Alternate install CD, and don't install GRUB to the Master Boot Record.

Ubuntu will create it's own partition, so unless you're shrinking a windows partition, defragging is not neccessary. I will presume you've defragged another windows partition on "G:"?

Usually the best thing to do is leave a large space (20 gigs is good for sure) of unused space, and tell the installer to install on the "largest continuous unused space". 

Take your sweet time with the installation steps, so you KNOW where Ubuntu is being installed, and of course, backup any valuable data.

---

### Post by edman2 on 2006-08-20
> **nalmeth said:**
> If you're really worried, you should backup any valuable data. If you know what you're doing with BIOS booting, then use the Alternate install CD, and don't install GRUB to the Master Boot Record.

Ubuntu will create it's own partition, so unless you're shrinking a windows partition, defragging is not neccessary. I will presume you've defragged another windows partition on "G:"?

Usually the best thing to do is leave a large space (20 gigs is good for sure) of unused space, and tell the installer to install on the "largest continuous unused space". 

Take your sweet time with the installation steps, so you KNOW where Ubuntu is being installed, and of course, backup any valuable data.

Yea G is a windows NTFS. It's a 120GB drive all of which is ntfs and used as storage in xp. What is the alternate install cd, and how do I not install GRUB?

---

### Post by edman2 on 2006-08-21
okay so i found the alternate install cd. A question about GRUB though, do I even need to install it? I mean am i techically dual booting, or can I just do as I said in the original post and just change the primary boot disk in the bios whenever I want to boot to xp or vice versa.

---

### Post by nalmeth on 2006-08-21
I don't know a whole lot BIOS booting honestly..
If however you do end up needing it to boot, you can just follow this guide to installing it:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by edman2 on 2006-08-21
Thanks nalmeth.

Does anyone else know what I need to do to install on my non boot drive G?

---

### Post by edman2 on 2006-08-21
Can't anybody help me out? Or am I just being an idiot?

---

### Post by edman2 on 2006-08-21
bump

---

