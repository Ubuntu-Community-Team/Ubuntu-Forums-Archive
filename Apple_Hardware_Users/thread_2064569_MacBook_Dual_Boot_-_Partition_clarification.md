---
title: "MacBook Dual Boot - Partition clarification"
date: 2012-09-29
forum: Apple Hardware Users
---

### Post by nobodyfamous on 2012-09-29
I have a MacBook, white (4,1) and did a dual boot install (using rEFIt)

I just created an 80 Gig "freespace" on the new SSD hard drive and then booted to a live USB of Ubuntu 12.04

here is the "stuff" for a "do something else" install;

/dev/sda1 efi
/dev/sda2 hfs+  (this is OS X)
/dev/sda3 fat32 (this is a partition I am going to use as a "swapbox" between OS X and Ubuntu)
free space 86033MB <- this is where Ubuntu will go.

I would like the 80 Gig space to hold Ubuntu and it's swap.  I am also totally confused about where to set the "Device for boot loader installation"

Thanks for the help, I just can't seem to find the answer anywhere.

I tried this once before and just used the "Install Ubuntu alongside Mac OS X" and it all worked, even used my free space to do it, but after selecting Ubuntu to boot to from rEFIt menu, I would get the boot menu from Ubuntu as well.  Is this the norm?

---

### Post by Lars Noodén on 2012-09-29
I would use HFS+ instead of FAT for the shared partition.  FAT is a poor technology and unsuitable to most tasks.  The journaling for HFS needs to get turned off for it to work with Ubuntu though.  You can get what you need in the packages hfsplus, hfsprogs, and hfsutils.

---

### Post by nobodyfamous on 2012-09-29
Thanks for the tip, I'll read up on it.

---

### Post by nobodyfamous on 2012-09-30
maybe I'll simplify my question.

If I do the "automatic" install alongside OS X - can I remove the boot menu? (the Linux/Ubuntu/GNOM one) So it just boots into Ubuntu normally after selecting it from the rEFIt menu.

---

### Post by Lars Noodén on 2012-09-30
I don't know of a way to eliminate grub or even if it is a good idea, but if you don't want to wait, you can shorten the countdown.

---

### Post by nobodyfamous on 2012-09-30
It's not so much that I want to remove it all together.  When I boot up our netbook, or the MacBook with ONLY ubuntu on it, it just boots up, no menu.  Only if it is a dual boot system does this menu show up.

If I can't have it not show up, and have to hit enter twice every time I boot to Ubuntu I guess I can live with it.

---

### Post by Lars Noodén on 2012-09-30
If you don't press anything then both rEFIt and Grub ought to just drop through to the default.  If both are set to Ubuntu then that's what you'll get without a keypress.  To get Ubuntu as the first choice in rEFIt instead of OS X, you have to use the [legacyfirst](http://refit.sourceforge.net/doc/c3s3_config.html) word in the configuration file.

---

### Post by nobodyfamous on 2012-09-30
I found some stuff about the grub menu - so I am just going to install Ubuntu "alongside OS X" and then edit the boot menu like you said. I should be able to set a hidden option and set timout to either 0 or 1.  Then you won't see the menu.

I need to make this simple for the wife.

---

