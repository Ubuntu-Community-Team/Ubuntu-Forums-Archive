---
title: "quick question about GRUB"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by swayer_77 on 2007-04-08
Right now I am dual booting Vista and Ubuntu. I also want to add OS X into the mix though. What would I need to do to fix the GRUB file after I install OS X on a new partition?

---

### Post by octoberdan on 2007-04-08
You might want to look over the first post and subsequent responses to [http://forum.insanelymac.com/index.php?showtopic=44974]("http://forum.insanelymac.com/index.php?showtopic=44974")

---

### Post by swayer_77 on 2007-04-08
This would help but I already have Vista and Ubuntu dual booting and would need to make an extra partition on my C: drive. Basically all I need to know is how I can get the GRUB file to allow me to select OS X, Vista, or Ubuntu after installing OS X last.

---

### Post by Patrick K on 2007-04-08
I think the easiest way, provided OS X is already installed, is to edit /boot/grub/memu.lst. You could add OS X below the "Other operating system" entry. You'd need to know the correct BIOS partition name. I don't know what other info you'd need. 

My "guess" for the entry is:
```
title		OS X
root		(hdx,x) (my edit, use the proper partition name)
savedefault
makeactive
chainloader	+1
```

This is a modified copy of the lines that load Windows on my system, your's will likely be a bit different. 

The BIOS partition name is slight different than the Linux name. For instance, Linux's hda1 is hd0,0 in BIOS speak. Notice the numbers are one lower.

---

### Post by dwblas on 2007-04-08
> after installing OS X last.Will this install the OS X boot manager? Probably.  Backup the MBR first, if you don't already know this, or review how to re-install GRUB from the live CD just in case.

---

