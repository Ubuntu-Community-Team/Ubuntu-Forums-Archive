---
title: "Dual booting"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by IngSoc on 2006-09-20
If I were to reinstall windows where would I take the partition from and what would I use to partition?

---

### Post by bulldog on 2006-09-20
Well you need a partition to install Windows.

If you don't have one, you could try to create one with gparted,BUT I can't guarantee it will work.
Chance is you mess up your Ubuntu as well.

Better option is to think about your configuration,BEFORE you install an OS.

---

### Post by roberto22085 on 2006-09-20
It sounds like you already have Linux installed. If so, you should really install Windows first and install Linux afterward. Linux tends to co-exist better with Windows than Windows with Linux. When you re-install Windows you will have an option to set up your Windows partition. I dual boot Ubuntu and WindowsXP. My hard drive is 160GB so I have 80GB set up for Windows and 80GB set up just for Ubuntu.

I hope that helps!

---

### Post by bodhi.zazen on 2006-09-20
:lol: This "Install Windows first" is over rated. I certainly would not advise you trash a perfectly good Ubuntu install now that you have one.

Why install windows at all? You can be very happy with Ubuntu no?

If you install windows second, as a part of the install, it will over write the MBR. You will need to re-install grub to the MBR and this takes less then 5 minutes from the Ubuntu CD.

The only requirement Windows has is that it needs to be installed into a primary partition.

---

### Post by bodhi.zazen on 2006-09-20
I got in a post before xpod....

He he...

---

### Post by bulldog on 2006-09-20
> **bodhi.zazen said:**
> :lol: This "Install Windows first" is over rated. I certainly would not advise you trash a perfectly good Ubuntu install now that you have one.

Why install windows at all? You can be very happy with Ubuntu no?

If you install windows second, as a part of the install, it will over write the MBR. You will need to re-install grub to the MBR and this takes less then 5 minutes from the Ubuntu CD.

The only requirement Windows has is that it needs to be installed into a primary partition.

Yes,and I'm afraid he has no primary left.

So he has a problem and I can't advice him without a warning to go fiddling with gparted.

---

### Post by IngSoc on 2006-09-20
Very pleased with ubuntu I just have some equipment that will need windows to operate and since im broke right now I cant buy a desk top to do my sound editing... I want to run reason and serato scratch.

---

### Post by bulldog on 2006-09-20
> **bodhi.zazen said:**
> I got in a post before xpod....

He he...

Yeah that's hard to do now a days,that guy is everywhere!:tongue:

---

### Post by xpod on 2006-09-20
> I got in a post before xpod...

I just doubled up on my ram today as well...SO god knows how you manged THAT!
Must be dodgy ram fae the dodgy ram dealer(you know WHO you are!)

---

### Post by Sef on 2006-09-20
Here's how to [reinstall GRUB.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Wien_Sean on 2006-09-20
Just a thought, but I would first defrag and then use Ghost to backup your setup onto a few disks. I am sure you can find a version of Ghost somewhere, legally I would assume. Now see if you can resize your linux partition. If that works then you should be able to install a minimal 2k/XP install. There are a few things you can do to slim down 2k or XP install with a program called nLite (it's free but it only works in Windows). I got my XP install down to about 500 mb.

---

### Post by IngSoc on 2006-09-20
sick

---

