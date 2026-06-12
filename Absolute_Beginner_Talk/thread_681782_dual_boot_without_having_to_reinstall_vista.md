---
title: "dual boot without having to reinstall vista"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Jmejme on 2008-01-29
ok im sure this is somewhere but nothing has quite answered my question.

I just got a new laptop and i know it will work with ubuntu. for the most part.
but thats not the problem. ok im not sure if it has the vista disk to re-install vista. (it just got shipped to home bout to go pick it up) but im going to assume it doesnt. it will already have vista on it. so how would repartition the 120gb harddrive without erasing vista to dual boot vista and ubuntu??? Please help :)
Thanks in advance

---

### Post by spiderbatdad on 2008-01-29
I don't think vista ships with a disk, however it ships with the ability to burn a recovery disk for yourself. A friend recently got a new vista machine, After several mishaps, he finally got the cd burning software to properly load his recovery partition...when he tried to burn, he got the message...You have already burned your free recovery disk. Opps.

Anyway Ubuntu installs with a partition editor that handles everything for you, if you like. But my friend also did a little research and said, there are problems partitioning Vista with non-windows editors...so I would get as much info in advance as possible, unless you are willing to lose Vista permanently.

---

### Post by cnlevo on 2008-01-29
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


there ya go. vista has a built in partitioning tool. it's pretty simple. I am dual booting ubunti studio with vista x64 ultimate and have no problems. GRUB loader does a great job.

---

### Post by ctswhole on 2008-01-29
You should have the option somewhere in the Vista control panel to burn a recovery disk.  To repartition your Vista hard drive without losing Vista, go to the Control Panel and look for (I believe it's called this) Administrator options or something like that.  There is a disk management thing there, something like Gparted.  You will have the option of shrinking the volume that Vista is on, leaving unallocated space on your hard drive to install Ubuntu on.  Hope this helps

---

### Post by obscur156 on 2008-01-29
Simple tutorial for dual,triple or quatro boot,wath ever you want to do.
Worked for my triple boot XP/GUTSY/HARDY.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Have fun with UBUNTU :guitar:

---

### Post by bumanie on 2008-01-29
Vista has its own in-built partition manager. You will have to shrink the vista partition with that and leave it is unallocatd space. You can get to the partition manager via right click on my computer --> disk management --> partition manager.
When loading ubuntu your best choice would be choose manual partitioning. It essential to have a /root partition and a /swap partition. Many people also make a /home partition where all their documents/music etc. is kept. The advangtage of a separate /home is that if anything went wrong with the 'base' operating system you would only have to install that and your  documents/music etc. would be untouched.

---

### Post by Jmejme on 2008-01-29
Thanks everyone for the quick replies!!!!

---

### Post by averagebeatboy on 2008-01-29
Is reinstalling Vista harder than Ubuntu?  Just curious as have XP and it is a pain to install because Microsoft misses a lot of software i.e., a fax et cetera.

Cheers,

Averagebeatboy   :guitar:

---

