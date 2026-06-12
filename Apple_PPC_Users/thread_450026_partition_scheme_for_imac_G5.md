---
title: "partition scheme for imac G5"
date: 2007-05-20
forum: Apple PPC Users
---

### Post by zapcojake on 2007-05-20
Hello, I am new to Linux on a PPC machine and have some questions regarding partitions.  Pretty much I need to know what I need.  I have a 150 gb hard drive with a 50g HFS+ for OS X, then a 20g ext3 for my Linux target a 128mb swap space and the rest for storage HFS+ .  There are some other partitions that show up in parted but I have no idea what I am looking at.  I am hoping somebody can explain what I need to do or point me to some reading on the subject.  I should also say that I am on a iMac g5 non-isight.

---

### Post by stmiller on 2007-05-20
Hey you should use Feisty, it has fixes esp for G5 machines concerning thermal management. Download link is in the PPCFAQs below.

And concerning the partitions, you should just leave blank unformatted space for Ubuntu and tell the Ubuntu installer to install into that space. It will automatically create the proper swap and root partitions. It will not delete or harm the other HFS+ partitions unless you force it to.

Can you possibly post a readout of what parted lists as your partitions? I can tell you what is safe to remove and such.

---

### Post by powerpc64 on 2007-05-22
Make a full disk clone with SuperDuper! or something like it.  On iMac you can use DVD-RW to backup data files.  In any case backup your data and OS.  If you have data in your Linux ext3, boot Linux and make a backup disc.

Use Ubuntu's alternate (text) installer and hit tab at the boot prompt to get boot options.  You want install-powerpc64.  Do not use the live CD.  Do manual partitioning.  Do not let Ubuntu decide for you.
[http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso)

The strange small partitions between the big ones are just Apple weirdness, leave them alone, they are necessary.  You'll see about twice as many partitions as you think you have.

Neglecting the Apple weirdness partitions, the ideal is

HFS+               OS X system and OS X swap
HFS+               OS X data
swap                Ubuntu swap     - 3 GiB
XFS                  Ubuntu /        - 10 GiB
XFS                  Ubuntu /home  - 100 GiB or whatever

The only Ubuntu partitions you want separated are /, swap, /home.  The /home one works like your OS X data partition, and can persist across Ubuntu version re-installs, etc.  Give all Ubuntu partitions labels, it will help later.

Use XFS filesystems and set option noatime.  I recommend against ext3 even though it's standard.  XFS is more stable and all Linuxes know it.  I crash things all the time and nothing ever happens to XFS data.  Ext3 is another story.

Your swap space is too small, give it a few gigs, you have them to spare.

Comment.  If you have Apple wireless mouse and keyboard, they will not work very well, if at all.  The gods of Ubuntu packaging need to roll up bluez 3.10 for PPC64.  You want usb.

---

### Post by 3rdalbum on 2007-05-22
3 gigabytes of swap is ridiculously huge. Many of us are former Mac OS 9 users, so don't we remember what we used to have set for virtual memory on OS 9?

The rule of thumb is: Virtual memory (or swap) should be no more than 1.5 times your actual RAM, or 512 megabytes; whichever is smaller.

512 megs is plenty - I've never used that much swap anyway. If Linux runs out of swap space, it starts storing swap data on your / anyway.

---

