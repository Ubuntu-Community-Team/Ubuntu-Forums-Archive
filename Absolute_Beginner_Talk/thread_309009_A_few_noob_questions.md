---
title: "A few noob questions"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by nenapod2 on 2006-11-29
Hello,
This may have been answered already but my searches were fruitless. Now, I have been wanting to try linux for a while. My first distro was a live cd called slax (slax.org). It worked okay, but WiFi and audio were not supported. I decided to try the ubuntu, the mother of all distros. My general questions are:
1.I want to keep Windows XP on my laptop. If I partition the HD (does it matter whether the new drive is ext2 or ext3?) and install on a partition, does it come with some sort of tool to help me choose an OS (os selector?)?
2.What can I do if Wifi doesn't work?
3.Is SigmaTel audio supported?

Thanks:D

---

### Post by b3tzi on 2006-11-29
1. Yes
2. Ask on the Forums
3. Dunno

---

### Post by koshari on 2006-11-29
> I want to keep Windows XP on my laptop. If I partition the HD (does it matter whether the new drive is ext2 or ext3?) and install on a partition, does it come with some sort of tool to help me choose an OS (os selector?)?
you could use ext2 or ext3, you might as well use ext3 as it has added journoling functionality, and is backwards compatable with ext2, also the installer will install grub for you which is a boot menu to choose what OS you want to boot.

> 
What can I do if Wifi doesn't work?
Cry? or otherwise scour the forums for an answer, posting your wifi chipset is a start, 



> Is SigmaTel audio supported?
pop in a live cd and find out.

---

### Post by nenapod2 on 2006-11-29
Wow, that was unbelievably fast! Thanks.

---

### Post by benuski on 2006-11-29
1. Yes, the installion installs the GRUB bootloader, which loads right after your BIOS does and will let you choose between Ubuntu and Windows.  As for the filesystem you use, it should really be ext3, and ext3 is just ext2 but more stable, up-to-date, and with a journal.
2. Most wifi cards, with enough work, can work at least somewhat on linux.  My internal Broadcom card doesn't work well with my encrypted school network, so my IT guy here gave me an older external one that works just fine.  Had I bought it, it would have only been about $20-30.  Or you can just use wired, ovs.
3.  I have no idea.

---

### Post by Sef on 2006-11-29
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for information on dual booting.

---

