---
title: "Gutsy: boot disk failure, can't mount additional hard drives."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by nicklikesfire on 2007-12-03
Hello,

everyone here has been extremely helpful so far, but I keep having problems, so thanks for being patient with me.

Anyways, I'm trying to install gutsy. I have a 200 gb ide drive that I want to use to install gutsy, I can reformat this and wipe it clean, doesn't matter. I also have 2 x 500 gb sata drives that I use for media. These are filled with my projects, and I can not format them.

I had dapper drake previously installed on a 40 gig hd, and the two media drives were working with this set up. I took the 40 gig hard drive out, and tried installing gutsy on the 200 gb drive.

I've tried using guided partitioning and manual partitioning, and both have the same results: when I restart I get the message "boot disk failure, insert system disk and press enter".

Even if I switch back to the 40 gig hard drive, I get the same result!

Now, I can leave the installation CD in when I boot up, and then that opens a menu with a choice "boot from first hard disk" which I select, and then I can get gutsy to boot.

Any idea how to solve this problem? I don't mind re installing or totally formatting the 200 gig drive.

Also, when I open up the file browser, I can see the two 500 gb disks, double clicking gives me an error "Unable to mount the volume 'Big Switch (465)'" I right click on them, and select mount, and then I get the same error.

any ideas?

Thanks, I'm pretty new and clueless about this whole thing. I really want to be using linux, and I really appreciate all the work that people put into this!

---

### Post by nicklikesfire on 2007-12-03
anyone?

---

### Post by OffAxis on 2007-12-03
Sounds like your boot flags aren't set up properly.
the easiest way is to use gparted to set/ remove boot flags on your drives.
You can get it here:
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Once you have the flags cleared, connect your drives like you want them and install normally.

---

### Post by nicklikesfire on 2007-12-03
> **OffAxis said:**
> Sounds like your boot flags aren't set up properly.
the easiest way is to use gparted to set/ remove boot flags on your drives.
You can get it here:
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Once you have the flags cleared, connect your drives like you want them and install normally.

So, I downloaded gparted-0.3.3.tar.gz and extracted it to my desktop... now what? like I said, I'm really new at this.

thanks!

---

