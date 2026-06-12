---
title: "Installing XP after Ubuntu"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by monkeymonkeymonkey on 2007-01-01
I've been running only Xubuntu now for 4 months, thought I wouldn't need my Windows XP partition so I deleted it. Now I need it back for a few applications.

I don't want to have to reinstall Xubuntu all over again to install XP first. I know I can use my gparted LiveCD to cut a 20GB partition for Windows but when I install XP it will delete GRUB.

How will I get grub back and allow myself to chose to boot Xubuntu or XP.

Thanks

---

### Post by oilchangeguy on 2007-01-01
are you using the factory restore disc, or a windows only disc? if it's a restore cd you'll have no choice but to reinstall ubuntu after you restore the factory image of xp. if you're using a windows cd (never tried this myself) you should be able, once you get the the setup page that displays any operating system already on the computer to create a partition from the free space not being used by the other os.

---

### Post by dfm21 on 2007-01-01
You surely have a Ubuntu Live CD at hand, that brings grub with it, so you should be able to install XP, overwriting grub, and reinstall it with the ubuntu cd. I never did it myself, but should be no problem.
See the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall") for information!
If you do it successfully, I'd love to see a HOWTO here.

Greetings!

---

### Post by Frank Golden on 2007-01-01
> **dfm21 said:**
> You surely have a Ubuntu Live CD at hand, that brings grub with it, so you should be able to install XP, overwriting grub, and reinstall it with the ubuntu cd. I never did it myself, but should be no problem.
See the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall") for information!
If you do it successfully, I'd love to see a HOWTO here.

Greetings!

See the following links. They are from a tutorial that I consider to be required reading 
for anyone considering dual booting.

[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)   this one is about the MBR

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)   this one is more than you will ever want to know about grub an how to restore after XP has removed it.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)     this last is about
Super Grub a tool you can download and make a bootable disk from that automatically
restores grub stage 1. This is the info on the MBR that XP overwrites. Stage 1 grub merely points
to stage 2 grub and the /boot/grub/menu.lst on your Ubuntu install.

One more link, this is the home page that these other links come from. If you have some time read the entire tutorial. Or at least bookmark it.
This tutorial is the brainchild of a Australian Ubuntu user. Everything you ever wanted to know about Dual Booting.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by monkeymonkeymonkey on 2007-01-01
Thanks Frank, it looks like super grub disk is the way to go. I'm going to try it out after backing up all my files and I'll post here when if I get get it working.

---

### Post by dfm21 on 2007-01-02
Thanks for the good looking references frank! If I ever want to install another OS, they surely will be coming handy!

---

