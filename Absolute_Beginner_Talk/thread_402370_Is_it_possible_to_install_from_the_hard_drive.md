---
title: "Is it possible to install from the hard drive"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by ssg_cope on 2007-04-05
I have a laptop with no cd rom, only floppy. is there a way to start the instalation with the floppy if i put the iso on the hd??

---

### Post by spin2cool on 2007-04-05
I don't know about that, but it's possible to do a network install, if you have another computer:  [http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)

googling for "ubuntu network install" will turn up about a dozen more sites with instructions

---

### Post by sirhalos on 2007-04-05
It is no longer possible to install Ubuntu from Floppy Disk. The installer is just too big, you can however use a USB flash drive. You can still install other Linux's such as Debian from Floppy Disk for a network install but the number of Linux's that you can do network installs is now very limited due to the fact the kernal itself can not fit on a signal floppy any longer. Is it possible to install Ubuntu from Floppy with a network install... Sure but you would need to create a customer kernel disk to do so with nothing hardly on it.

---

### Post by LaurelLynn on 2007-04-05
You could also purchase a usb cdrom, at a resonable price, which might work with your laptop (depends on how old it is,  floppy only sounds old).

Laurel Lynn

---

### Post by sirhalos on 2007-04-05
I work at the Micro Center copoarte office we have 1 gig USB flash drives priced at $9.99 and 2 gig USB flash drives for $15.99 so yes they are cheap.

---

### Post by sirhalos on 2007-04-05
I thought of another way to do it but it's going to be ugly bare with me. "IF" you wanted to use 2 partitons you can use partition magic in Windows so you have a second partition then use VMware and tell it to use the physical hard drive, download the ISO, boot from ISO and install to that partition. Very dangerous to do this but it can be done, people have done this method for MacOS X Intel installs. There are directions on ox86projects website due to the nature of the website I am not providing a link.

---

### Post by ssg_cope on 2007-04-05
it had a cd rom but it broke, it has usb but cannot boot from usb, is there a way i can start it with a floppy from the cdrom?

---

### Post by LaurelLynn on 2007-04-05
In that case, I would copy the ISO off of the CD from another computer on your companies network, then search for how-tos on PXE installs.

Even if you install an old floppy based version of linux you will still need a network to get Ubuntu over to the laptop. There is no practical way to fit 600-700MBytes on floppies. At least that I can see.

Laurel Lynn

---

### Post by daveb272 on 2007-04-07
i need to know it it is possible.  i have a tablet pc with no floppy or cd.  also it doesn't support usb boot.  i copied the entire contents of the cd to the hd.  i can get to a dos prompt by pressing f8,  what would i need to find to install it ie a setup file or (exe)?

---

