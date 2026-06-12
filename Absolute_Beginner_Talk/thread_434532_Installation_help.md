---
title: "Installation help"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by jingdejun on 2007-05-06
Hello all,

I am a newbie to Unix. Now I am trying to install Ubunto 7.04 Desktop edition. 

I have two physical hard driver installed in my computer. The first disk is now for Windows XP with three partitions. Now I plan to install Ubunto Feisty on the second disk. I hope to keep WinXP and Ubunto coexist for my machine, ad there will be a OS-selection menu when I start the computer. 

Before I install ubunto, I would like to get some suggestions to following questions:

(1) Is there any specific thing that I need to do with partition during installation? Or since I am using a separate physical disk for Ubunto, I do not need to care about partition?

(2) The OS-selection menu will be automatically generated or I need to create it manually? If later, how shall I do?

(3) I am using ATI X600 video cards. From posts in this forum it looks like Ubunto installation have problem with ATI card. Is there a way or guide to bypass this problem?

(4) I tried to find detailed installation guide for Ubunto Feisty, but can not. ANyone can provide a link to a good installation guide?

Thanks a lot for answers.

Regards,
Derek

---

### Post by Duck2006 on 2007-05-06
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by rygar on 2007-05-06
1) the Ubuntu installer should give you an option as to which disk you want to install the OS to.  if it doesn't, you can always select 'manual' during the partition step and set it to your secondary hard drive (probably something like /dev/sdb)

2) GRUB, the boot manager that comes with Ubuntu, should be installed by default.  you shouldn't have to do anything.

3) yes, you probably will have problems.  there's no way to "bypass" this, but there are lots of tutorials on this forum, as well as helpful users, which can probably get your card running right.  i'd say install the OS, then worry about getting your video card working.  you can always go back to XP if you want.

4) not sure, sorry.  the installation is pretty user-friendly though.  the only tricky part for many dual-booting users is the partition step.  be careful about what you select as to not overwrite your XP partition.  you may want to back up your important data to be safe.

---

### Post by antoz on 2007-05-06
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This is another good link, normally after installing you get the grub menu to select what OP you want to boot but I am not sure because your Ubuntu install is on a different drive you may have to set up grub manually afterwords or change the boot order in the bios so it points to the drive where Ubuntu and grub reside.
hope this helps,A

---

### Post by candtalan on 2007-05-06
>I am a newbie to Unix. Now I am trying to install Ubunto 7.04 Desktop edition.

Welcome!

>I have two physical hard driver installed in my computer. The first disk is now for Windows XP with three partitions. Now I plan to install Ubunto Feisty on the second disk. I hope to keep WinXP and Ubunto coexist for my machine, ad there will be a OS-selection menu when I start the computer.

>Before I install ubunto, I would like to get some suggestions to following questions:

>(1) Is there any specific thing that I need to do with partition during installation? Or since I am using a separate physical disk for Ubunto, I do not need to care about partition?

If you begin with the live CD and run it, this shows that your hardware and graphics will work. Then you can choose the install icon.

The install process gives a choice of where to install - you can choose hard drive hda or hdb or similar. Note carefully that the default option may delete windows, so read and choose carefully. Your drive hdb should be your second new spare drive - check the size  and identity looks correct to confirm your choice and understanding. You can then proceed using the automatic process (not the manual process). I do not think you have further partition decisions because you will have said that ubuntu can completely take over your spare drive (hdb) which is not formatted yet and contains only unallocated space. On the linux drive there will be two partitions created - a smaller swap partition and a larger system partition.

>(2) The OS-selection menu will be automatically generated or I need to create it manually? If later, how shall I do?

It will be automatcally created. I will be based on the Grub approach, and may be edited at a later date if you want to change things.

>(3) I am using ATI X600 video cards. From posts in this forum it looks like Ubunto installation have problem with ATI card. Is there a way or guide to bypass this problem?

The use of the live CD initially is important and useful for looking at this. If you need a problem solved, then do it with the live CD immediately before install if you can.

good luck

---

### Post by candtalan on 2007-05-06
> **antoz said:**
> [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This is another good link, normally after installing you get the grub menu to select what OP you want to boot but I am not sure because your Ubuntu install is on a different drive you may have to set up grub manually afterwords or change the boot order in the bios so it points to the drive where Ubuntu and grub reside.
hope this helps,A

I believe grub will accept different drives no problem, with no editing.

---

