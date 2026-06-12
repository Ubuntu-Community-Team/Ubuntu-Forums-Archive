---
title: "Partimage locally?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-03-31
I've been looking into backing up my partition, somebody told me about partimage.

He said you can run it off the rescuecd (which I dl'ed) to recover a partition - but what about storing it?  Do you need to boot the rescue CD to backup the image - or can you install partimage locally (on the partition you're backing up) and run it to back up to a different location.

ie.  Can I install partimage locally on the partition that I'm using to type this (my daily partition) to back it (the whole partition) up to a different hard drive?  Or do I have to boot the CD and do it "outside" the partition?

---

### Post by abhiroopb on 2008-03-31
Information on partimage: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I would recommend having the rescueCD handy in case your hard drive (with partimage on it) gets corrupted. But I do not know how you would put it on the partition.

---

### Post by indytim on 2008-03-31
As you have found out, you cannot run Partimage against your booted partition.  As far as storage, you will want to store your backed up images in a partition other than your ops.  In the event that your ops partition needs to be restored, you don't want to have the image residing in the same partition.

IndyTim

---

### Post by abhiroopb on 2008-03-31
I use partimage extensively and I recommend buying an small portable hard drive and using that to backup everything to (this can also be used if your laptop is lost/stolen).

---

### Post by Syndacate on 2008-04-01
Okay, I'm relatively confused by the answers so I'm going to assume I asked the question in a poor way.

First off, somebody said something about laptops, this is my desktop.

Secondly, somebody was talking about storing the image on the same partition - that doesn't make any sense what-so-ever.

Also, what is an "ops partition?"

Here's my goal:
I have two hard drives in my computer, one's a windows/ubuntu hard drive, the other is nothing as of now (an old non-working windows system).

I'd like to back this ubuntu partition up to that second hard drive, though not just for recovery - I want to use partimage sort of like ghost - to create an image backup every week or so of this partition so if everything falls apart I can get a new hard drive, slap it in, and reload the image back on it.

I realize to re-load the image back on it I'm going to need the rescue disk, though I'm asking if I could use partimage locally to back the image up to the other hard drive weekly or whatever.  Or when I want to back it up do I need to boot off the rescue CD, and use partimage to back it up manually, and then boot back onto this partition?

Either way will do, just having it locally to back up with is less of a hassle, which is why I'm asking.  Though if I need to boot off the CD to make backups - I will.

---

### Post by logos34 on 2008-04-01
No, you'll have to boot from a CD--the partition you're backing up with partimage cannot be mounted.

The only way to make an image of root without having to boot from a CD is to put the disc containing Partimage on a separate partition and boot from that (which is how I have mine set up--no need to fiddle with CDs), but you still have to reboot to run it.

---

### Post by Syndacate on 2008-04-01
> **abhiroopb said:**
> Information on partimage: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I would recommend having the rescueCD handy in case your hard drive (with partimage on it) gets corrupted. But I do not know how you would put it on the partition.

Thanks, the link helped a lot.

I have the image of the rescue CD (just been too lazy to burn it), but I'll burn it before I attempt anything, of course.

From the look of the that site, you can't back up a partition locally, you have to do it outside the partition.

Though it says you have to mount the backup partition.  I still a pretty big UNIX newbie, the way I understand mounting - it should already be mounted, right?

I mean my fstab file is ****** up beyond belief - but it works.  I can still minimize this window and access the drive that I'm going to be backing this up to - I didn't add it to the fstab - I'm assuming Ubuntu has some auto-mount thing...Anybody wanna fill me in here if I do or don't have to re-mount this?

---

### Post by Syndacate on 2008-04-01
> **logos34 said:**
> No, you'll have to boot from a CD--the partition you're backing up with partimage cannot be mounted.

The only way to make an image of root without having to boot from a CD is to put the disc containing Partimage on a separate partition and boot from that (which is how I have mine set up--no need to fiddle with CDs), but you still have to reboot to run it.

Ahh, smart.  I might do that at some point but for now I don't mind messing with the CD's.  I do believe I can use gparted to make a small partition of like 1gb, right?  Then I can just mount the .iso (raw image) there?

Though how do you tell it to boot off of that partition instead of attempting to boot regular - like you gotta add it to GRUB or something, no?

---

### Post by logos34 on 2008-04-01
> **Syndacate said:**
> Ahh, smart.  I might do that at some point but for now I don't mind messing with the CD's.  I do believe I can use gparted to make a small partition of like 1gb, right?  Then I can just mount the .iso (raw image) there?

Though how do you tell it to boot off of that partition instead of attempting to boot regular - like you gotta add it to GRUB or something, no?

Mine's only 100 MB (actually it started out as a separate grub partition).  Just add an entry to menu.lst and select that at boot.

[http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk](http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk)
[http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm](http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm)

---

### Post by Syndacate on 2008-04-02
> **logos34 said:**
> Mine's only 100 MB (actually it started out as a separate grub partition).  Just add an entry to menu.lst and select that at boot.

[http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk](http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk)
[http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm](http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm)

But you just did it with a raw image (.iso), right?  How did you name that image within the partition to boot?  You just changed the location to that partition ie. (hd0,2), left the kernel path alone, and changed the initrd path to reflect that of your .iso?

---

### Post by logos34 on 2008-04-02
> **Syndacate said:**
> But you just did it with a raw image (.iso), right?  How did you name that image within the partition to boot?  You just changed the location to that partition ie. (hd0,2), left the kernel path alone, and changed the initrd path to reflect that of your .iso?

No, you need to copy the files inside the iso to the drive.  It's all in the links I gave you above.  I'm pretty sure I followed them to in setting up gparted and parted magic hard disk boot.  Here's what my menu.lst entries look like (my separate grub partition is hda3):

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Boot from CD (SBM)
root            (hd0,2)
kernel          /boot/memdisk
initrd          /boot/sbm.img

title [COLOR="Red"]Parted Magic 1.8[/COLOR]
root (hd0,2)
kernel /isolinux/bzImage root=/dev/ram0 initrd=initrd init=/linuxrc ramdisk_size=100000
initrd /isolinux/initrd.gz

title [COLOR="Red"]Gparted 0.3.3-0[/COLOR]
root (hd0,2)
kernel /isolinux2/linux root=/dev/ram0 initrd=initrd.gz init=/linuxrc ramdisk_size=65000
initrd /isolinux2/initrd.gz

---

