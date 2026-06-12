---
title: "Dual boot on seperate HDD's?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Dj Dutchman on 2007-06-02
Is its possible to install a dual-boot ubuntu/XP but on different HDDs? In other words ubuntu on one HDD and XP on another and having the option of which one to boot from at boot up...

Many thanx :)

---

### Post by overdrank on 2007-06-02
> **Dj Dutchman said:**
> Is its possible to install a dual-boot ubuntu/XP but on different HDDs? In other words ubuntu on one HDD and XP on another and having the option of which one to boot from at boot up...

Many thanx :)

Hi and yes it is! I have the same setup on one system with two drives and four partition between them. ;)

---

### Post by Dj Dutchman on 2007-06-03
And how do you do it?

---

### Post by oilchangeguy on 2007-06-03
here's how i did mine. first did a clean install of xp pro (legal copy) on a hard drive jumpered as master. then removed that drive installed second drive jumpered as master. did a clean install of ubuntu 6.06. re-installed the windows drive, jumpered as slave. rebooted the computer, and grub gave the option to boot into either os.

---

### Post by Dj Dutchman on 2007-06-03
But that would only work if you runnin IDE HDD's (cuz SATA drives dont have Master/Slave jumper settings). What if im running one IDE and one SATA?

---

### Post by oilchangeguy on 2007-06-03
> **Dj Dutchman said:**
> But that would only work if you runnin IDE HDD's (cuz SATA drives dont have Master/Slave jumper settings). What if im running one IDE and one SATA?

i'd use the ide drive for windows, set it to cable select. just make sure that the bios shows the sata drive as the first hard drive in the boot order.

---

### Post by Dj Dutchman on 2007-06-03
I mite be wrong but surely then, it will run the ubuntu drive all the time until you change the boot order in the BIOS?

---

### Post by oilchangeguy on 2007-06-03
> **Dj Dutchman said:**
> I mite be wrong but surely then, it will run the ubuntu drive all the time until you change the boot order in the BIOS?

no, grub will give you the option to boot into either os.

---

### Post by confused57 on 2007-06-03
This may be an option for you:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

The tutorial is for IDE drives, but the principle should be the same for SATA...your system would be set up to boot the Ubuntu drive first.

---

