---
title: "prepare partition for vista"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by bibas on 2008-03-04
hi,
i have vista preinstalled in my laptopand have no extra partitions except c:
HOw do i resize it to make a room for ubuntu installation? I cant do it by partition magic like in win XP.It seems to be primary partition which doesnt want to change.

---

### Post by jan quark on 2008-03-04
have a look at this guide:
[LIST]
[*][http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[/LIST]

---

### Post by bibas on 2008-03-04
nice post
thank you

---

### Post by housam on 2008-03-04
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.( you already have two of them , one has windows and the other for the recovery )
-I suggest to create one more primary partitions for your data and another one as extended partition which can be devided to many logical partitions (resizing windows partition and creating two new partitions)
- the extended partition can be devided to 2 partitions : one EXT3 ( 10 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

### Post by hyper_ch on 2008-03-04
Use the VISTA Partitioner to resize the VISTA partition!

---

