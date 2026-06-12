---
title: "Dual Booting and Vista SP1"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by gubemton on 2008-02-22
Hello, 

I would like to ask a question. I heard that Vista SP1 may affect a dual boot system, I do not remember the specific details. But, anyway, I was wondering if anyone had a dual boot with Gutsy because I would like to try Ubuntu again.

---

### Post by Presto123 on 2008-02-23
You currently have Vista loaded? I do, and it doesn't have any issues here except for not releasing my audio card on reboot. Simple fix though, just shut down completely and start it up again. Some users DO have issues trying to dual-boot.

Give us some hardware specs on your system.

---

### Post by Yoke &amp; Chung on 2008-02-23
Should not have any problem, I have done that with Vista/ Gutsy (not SP1 though).

One experience to share:
Do NOT allow Ubuntu to re-partition your hard disk during the installation, the Vista may not boot if you do that. Use your Vista built-in partitioner to shrink the hard disk, then install Ubuntu into the free space.

Good luck!

---

### Post by gubemton on 2008-02-23
I have an Acer 5100-5030

AMD Turion @ 2Ghz
2Gb of Ram
160GB HDD
ATI X1100 (Integrated)

I used to have a Vista/Gutsy dual boot but I reformatted the entire drive and just put Vista on. I recently acquired SP1, but am weary to try to dual boot because I heard that SP1 introduced something that may adversely affect the dual boot. I think it was called bit-locker or something. Anyway, thanks for the help so far. Still need some more.

---

### Post by ssican on 2008-03-26
News of APC Magazine,  26 March 2008:

"VISTA SP1 WON'T INSTALL ON DUAL-BOOT SYSTEMS":

[http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm](http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm)

---

### Post by camini on 2008-03-26
No problem here.  Installed SP1 last week on my vista ultimate and dual boot (grub based) still works fine.

---

### Post by Miljet on 2008-03-26
I guess that will be the reason I was waiting for to completely wipe Vista off my hard drive!

---

### Post by DXM31 on 2008-03-26
I updated to SP1 on Vista Premium and have had no problems dual booting.

---

### Post by rkd on 2008-03-27
According to the article pointed to in post #5, the problem occurs only with Vista Ultimate or Vista Enterprise, so if you have any other version, you won't have a problem.  And the workaround if you do have the problem is very simple -- check that article to see what it is.

---

### Post by N1N31NCHN41L5 on 2008-03-27
I'm running a HP Pavilion Elite with Vista preloaded. I let Ubuntu repartition my HDD and load Ubuntu on the new part. Works Great, no issues so far. Vista Home Premium.

---

### Post by lswest on 2008-03-27
I installed SP 1 on my vista too, only problem was it wasn't installed by the windows update, but i downloaded the file from microsoft.com, then ran it and it installed no problem...i have yet to notice any benefit of this though lol

---

### Post by rkd on 2008-03-27
To anyone installing Ubuntu for dual-boot on a Vista machine:

It is much better to use Vista's disk manager to shrink the size of the Vista partition rather than letting Ubuntu do it.  I don't know what factors matter, but at least in some cases, things don't work at all well if you let Ubuntu do the resizing.

It is okay to let Ubuntu set up the partitions it needs in the unused space after you have used Vista to shrink the Vista partition.  Just don't try to shrink Vista's partition with Ubuntu.

---

### Post by ghost_ryder35 on 2008-03-27
I'm Dual booting Gutsy 64bit and Vista Buisness with SP1 64bit and DO NOT have any problems at all.

---

### Post by bknorr on 2008-04-01
I wish I had read this thread yesterday. Hardy ate my Vista sp1. Loaded Hardy with no problems. When I switched back to Vista home premium I found MBR error. I needed to clean system anyway:)

---

### Post by Duck2006 on 2008-04-01
> **bknorr said:**
> I wish I had read this thread yesterday. Hardy ate my Vista sp1. Loaded Hardy with no problems. When I switched back to Vista home premium I found MBR error. I needed to clean system anyway:)

Install vista and then follow this link for the install of ubuntu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

