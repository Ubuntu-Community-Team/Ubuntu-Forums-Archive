---
title: "errror 20 on dual boot xp ubuntu may 07 on 2d hdd"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Duane A on 2008-03-22
For 3 months I have not been able to access ubuntu due to error 20. In my case the bios starts grub and then stalls and says error 20. 

I can not get a terminal, it just hangs. 

On xp using win explorer or my computer, I can get no recognition of disk 2. The bios says it is there. 

Do you have any options for a ubuntu dummy? Just to get access to Ubuntu thru boot. Below is just whining about it's problems. I think I need to re-install or delete.

I would like to erase the whole 2nd disk and reinstall a later ubuntu as 7.04 is seriously deficient. Won't upgrade, won't run .mva files,won't type the letter s to get sudo or anything else in terminal. It will if I copy an 's' from notebook but this is a drag.

---

### Post by tvtech on 2008-03-22
check this link out it gives you the grub error list.  

[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")

which stage is it? 

error 20 = Multiboot kernel must be loaded before modules
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of such modules to a non-Multiboot-aware kern

I would highly recommend a reinstall 7.10  is a VAST improvement over 7.04   and 8.04 should be a VAST improvement over that.  7.10  in my opinion is the first fully functional version of ubuntu that really makes using it easy since I installed it I haven't booted into windows for anything at all. except to check compatibility with my smb server that I run.

also you can't access ext3 natively by windows the disk won't show up in many cases.  There are a couple free drivers you can install to recover data if necessary  ext3ifs
[http://www.fs-driver.org/]("http://www.fs-driver.org/") is really useful for this

---

### Post by dstew on 2008-03-22
What is the exact error message? Is it just the number (stage1.5) or does it also include an explanation (stage2)? Do you ever see the grub menu?

---

