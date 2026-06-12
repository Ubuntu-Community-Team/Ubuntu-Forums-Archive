---
title: "EXT4 with Arch Linux...how?"
date: 2009-01-20
forum: Arch and derivatives
---

### Post by gjoellee on 2009-01-20
I installed GRUB2 and it seams to work fine. However I would like to get the Ext4 filesystem on my computer. I just can't find out how? Can anyone give me an easy tutorial please?

---

### Post by mips on 2009-01-20
Maybe have a look at this,
[http://wiki.archlinux.org/index.php/Ext4#Converting_From_ext3_to_ext4](http://wiki.archlinux.org/index.php/Ext4#Converting_From_ext3_to_ext4)
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
[http://www.ibm.com/developerworks/linux/library/l-ext4/index.html](http://www.ibm.com/developerworks/linux/library/l-ext4/index.html)

---

### Post by ghindo on 2009-01-20
So GRUB 2 is stable, then?  I thought it was in an indefinite holding pattern for the time being.  How do you install it from an existing Arch install?

---

### Post by mips on 2009-01-20
> **ghindo said:**
> So GRUB 2 is stable, then?  I thought it was in an indefinite holding pattern for the time being.  How do you install it from an existing Arch install?

[http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)

---

### Post by ghindo on 2009-01-20
> **mips said:**
> [http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)> The next generation of the GRand Unified Bootloader (GRUB2) is still under development and therefore all usual points apply. **GRUB2 may fry you computer, burn your house, or eat your cat. You've been warned!** For most people, except those with more exotic configurations, GRUB2 should just work.Huh.  When is the final release supposed to be?  And what is everybody's experience with GRUB 2?

---

### Post by mips on 2009-01-20
> **ghindo said:**
> Huh.  When is the final release supposed to be?  And what is everybody's experience with GRUB 2?

No idea, all I know is there are a good few people using it already.

---

### Post by gjoellee on 2009-01-20
Thanks...And how fast that is done when you dualboot! Used under 10 min! Things are getting noticeable faster!

NOTE: The "Mark thread as solved" is gone

---

### Post by ghindo on 2009-01-20
[http://bbs.archlinux.org/viewtopic.php?pid=482797#p482797](http://bbs.archlinux.org/viewtopic.php?pid=482797#p482797)> Last time I checked grub2 was not able to handle the extents of ext4. But grub from [core] does.Interesting.  So you don't even need grub2 for ext4 (at least in Arch).

---

### Post by fwojciec on 2009-01-20
The procedure I just used to switch my desktop's rootfs to ext4:

[LIST=1]
[*]Get a live CD with ext4 support (like systemrescue cd 1.1.4 or more recent)
[*][might be necessary with default kernel, I'm not sure] Make sure that you have the latest kernel26 package installed; edit mkinitcpio.conf and add ext4 to MODULES array; regenerate kernel images with mkinitcpio
[*]Boot using the live CD
[*]Backup root filesystem to a tar file on a different partition
[*]Delete the old root fs and create a new ext4 fs in its place (Arch wiki has a section on how to do it)
[*]Untar the previously backed up fs onto the newly created ext4 fs
[*]Edit fstab file on the newly extracted fs, change the root partition type to ext4
[*]I also needed to add rootfstype=ext4 to kernel command line in grub's menu.lst to avoid a non-fatal warning on boot.[/LIST]

That's pretty much it.  The whole tar/untar method for cloning filesystems is explained in this [guide]("http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning") -- the guide was written for Red Hat, I think, but it's easy to adapt it to Arch's conventions.

It's a bit of an ordeal, and if something goes wrong you're likely to end up with a kernel panic on the first boot.  Still, I've done this many times and it should be completely safe when done properly.

---

### Post by smartboyathome on 2009-01-21
By the way, I am now on EXT4! Runs great! Thanks, SysRescueCD and the Arch Linux Wiki. ;)

---

