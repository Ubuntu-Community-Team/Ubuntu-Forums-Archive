---
title: "Partitions/partition sizes for dual boot with Windows XP already installed"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by getitright on 2008-04-19
My HDD is 300Gbs.

I propose to partition the HDD as follows:

**Windows XP**

**Ubuntu/home (ext 3)** (for shared data)

**Ubuntu/ (ext 3)**

**Ubuntu/boot**

**Ubuntu/swap** (Installed RAM is 2Gbs)

What advice can be given for the size of partitions?

Would it be better to substitute a NTFS partition for the Ubuntu/home for shared data?

---

### Post by sancho panza on 2008-04-19
The partition sizes of windows and ubuntu home depend on how much stuff you intend to put on each of them. If you intend to use ubuntu often, I would strongly suggest ext3 for /home as it is supported natively and ntfs tends to fragment over time. Use another ntfs drive (the windows partition itself) for sharing files; or use software in windows that lets u read ext3 drives.

10 gigs for /,
512megs or less swap as u wont probab need it if you dont uses graphics or computationally intensive programs that would need more than 2gigs of installed ram.
/boot: I dont know

Cheers,

---

### Post by george9233 on 2008-04-19
I think /boot need no more than 50M since my /boot folder is just 17M.

---

### Post by zvacet on 2008-04-19
You don´t need boot if you have root (mountpoint /).And you don´ need more then 1GB for swap.To make your windows see ubuntu install in windows [this.]("http://www.fs-driver.org/")

---

### Post by prshah on 2008-04-19
> **sancho panza said:**
> 
10 gigs for /,
512megs or less swap as u wont probab need it if you dont uses graphics or computationally Cheers,

> **zvacet said:**
> You don´t need boot if you have root (mountpoint /).And you don´ need more then 1GB for swap.To make your windows see ubuntu install in windows [this.]("http://www.fs-driver.org/")

You need atleast as much swap as you have RAM, if you intend to use the hibernation feature, since the hibernation image is stored to your swap. Besides, since you have so much space, better to allocate some more swap rather than try resizing later if you need it. 

I'd say 2Gb or 2.2Gb is fair for swap in this case.

---

### Post by getitright on 2008-04-19
> **zvacet said:**
> You don´t need boot if you have root (mountpoint /).And you don´ need more then 1GB for swap.To make your windows see ubuntu install in windows [this.]("http://www.fs-driver.org/")

Does this mean that the boot (GRUB?) files will be installed on the root/ partition when running Ubuntu setup?

---

### Post by zvacet on 2008-04-20
It will be install on [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") and to boot windows you will have to make some changes in grub.Nothing difficult.Let me know when you come to that step.

---

### Post by halln on 2008-04-20
try this nice link:  [http://www.linux.com/feature/114157](http://www.linux.com/feature/114157)

---

### Post by sandysandy on 2008-04-20
some links

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

