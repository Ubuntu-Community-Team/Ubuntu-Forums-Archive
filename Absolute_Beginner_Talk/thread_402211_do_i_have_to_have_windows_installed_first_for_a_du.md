---
title: "do i have to have windows installed *first* for a dual boot?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by sit properly on 2007-04-05
I've been using Ubuntu for about a month on my laptop. It is fully Ubuntu. 

But I need two programs that I can't make run in linux, so I'll have to dual boot. Not a big problem, but do I need to install windows over Ubuntu and then install Ubuntu again losing everything that I've installed under Ubuntu (not a huge deal, but still a pain)?

I have a feeling that Windows will "eat" Grub (at least). But maybe there's a work-around?

---

### Post by oilchangeguy on 2007-04-05
are you using a system restore disc, or a windows only disc?

---

### Post by .Morpheus on 2007-04-05
> **sit properly said:**
> I've been using Ubuntu for about a month on my laptop. It is fully Ubuntu. 

But I need two programs that I can't make run in linux, so I'll have to dual boot. Not a big problem, but do I need to install windows over Ubuntu and then install Ubuntu again losing everything that I've installed under Ubuntu (not a huge deal, but still a pain)?

I have a feeling that Windows will "eat" Grub (at least). But maybe there's a work-around?

M$ Windoze does not respect any non-windoze partitions, but in the XP installer, I think its possible to install it on a partition by it self.  However, I've never installed XP fully.  I tried and gave up.  Ubuntu took me 20 minutes =D.

---

### Post by sit properly on 2007-04-05
Ubuntu's install is just wonderful. 

I'm using an XP Pro disc, not a system restore. 

I'm also running Edgy, but that probably doesn't matter.

---

### Post by Pikestaff on 2007-04-05
From what I've heard it's preferable to set up a dual-boot when you have Windows installed first (because yeah, Windows eats Grub) but it's possible to do it starting with Ubuntu first.  I'm not exactly sure how, I'm afraid, but it is possible.

---

### Post by oilchangeguy on 2007-04-05
you'll need to run your ubuntu live cd, and use gparted to set up a partition for windows. then from your xp cd install windows on the partition you created with gparted.

---

### Post by anaconda on 2007-04-05
Yep. It definetely is possible. I have done it with windows 2000 and the only problem was that windows overwrote the grub.

---

### Post by rsambuca on 2007-04-05
> **oilchangeguy said:**
> you'll need to run your ubuntu live cd, and use gparted to set up a partition for windows. then from your xp cd install windows on the partition you created with gparted.Correct, and then re-install grub from the ubuntu CD.  One minor change on partitioning -> I would recommend using the gparted live CD, as it is a little more current than the one on the ubuntu disk.

---

### Post by xdarkxanarchyx on 2007-04-05
Or, after installing Windows you can use [SuperGRUB Disk]("http://supergrub.forjamari.linex.org/") and it will find your OSs again and reload GRUB if you want it to. I find this to be a good method, it's always worked for me. There might be a newer version of it by now too.

---

### Post by sit properly on 2007-04-05
thanks! I checked out GNUparted and seems easy, but Super Grub seems easier. I'll give that a shot. 

Thanks!

---

### Post by rsambuca on 2007-04-05
> **sit properly said:**
> thanks! I checked out GNUparted and seems easy, but Super Grub seems easier. I'll give that a shot. 

Thanks!
Just keep in mind that gParted is for partitioning your hard drives, and Super Grub is for configuring the boot-manager.  They are both very handy utilities to keep around.

---

### Post by garybrlow on 2007-04-05
Install Windows on another partition. The windows boot loader will most likely replace Grub. You can set the windows boot.ini to reflect ubuntu on it. But its easier to just restore Grub using Ubuntu Live CD. Its easier to Install windows first on Primary partition then Ubuntu second to so that Grub will take over the windows boot loader.Just keep in mind that Kernel image  changes and other grub options can not be seen nor accessed via windows boot loader so its better to use grub.

Cheers!!!


GaryBrlow :biggrin:

---

