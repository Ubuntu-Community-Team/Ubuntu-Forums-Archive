---
title: "Installation without wiping out HDD?"
date: 2007-07-11
forum: Apple PPC Users
---

### Post by kevipapo1 on 2007-07-11
Ubuntu is hell to me.  Pure hell.  I burned feisty faun to a cd with disk utility, it boots up normally, open install, choose the recommended installation, and my HDD gets wiped out.  I didn't know it would happen.

I've laft 10GB of my HDD free for Linux.  Just open space.  The other way I would have installed would have been to partition my drive, but everytime I try to install that way I get the most annoying message ever:

"No NewWorld boootpartition was found.  Ubuntu requires an Apple Bootstrap..."

I don't remember the rest but the same thing happened with 6.10.

I'm about to blow my head off.  Can someone give me some straightforeward instructions on how to fix this problem?  What are the exact commands to use in Terminal, or whatever?  I really want this to get done.

I have a PowerBook G4 12-inch 1.5 GHz 512 MB DDR SDRAM.  The startup disk is Mac OS X (that's what I called it), and I have 10GB of free space on the hard drive.  It's not a partition, it's just a blank space on the hard drive.

Thanks for any/all help!

---

### Post by shawnhcorey on 2007-07-11
First, you may have to resign yourself to the fact that your hard disk is totally screwed and a completely re-install may be the only thing you can do.

Recently I messed up my upgrade to 7.04 but I was able to recover the data off my disk:  [http://www.magma.ca/~shawnhcorey/200707/1183732322.html](http://www.magma.ca/~shawnhcorey/200707/1183732322.html)
I still had to re-install everything.

---

### Post by kevipapo1 on 2007-07-11
This I tried, but working with partitions in Terminal isn't my thing.  I'm willing to backup my HDD and install Linux over everything.  After the installation of Linux I want 65GB for Mac OS X and 10GB for Ubuntu.  Can someone give me terminal commands to get that to work plz?

Also, I'm going to back up my whole drive, including the library, plugins, etc...Let's say I installed Mac OS X from the install DVD, then I drag all the files from the backup over to my computer, would all my apps be updated?  What about when you upgrade from 10.4.3 to 10.4.10 of Tiger, will drag and drop back onto my computer work and I would have the updates?

---

### Post by shawnhcorey on 2007-07-11
If you boot Ubuntu from CD, you'll find a GUI partitioner under the System -> Administration menu.

---

### Post by pxwpxw on 2007-07-11
Hi,
What have you got installed now - macosx or ubuntu?

---

### Post by kevipapo1 on 2007-07-11
I'm using Mac OS X right now.

---

### Post by pxwpxw on 2007-07-11
> **kevipapo1 said:**
> I'm using Mac OS X right now.

In that case, can you open the macosx  terminal.app from applications or utilities, and see exactly what your disk partitions are with these two command lines
```

 diskutil list
 sudo pdisk -l

```
Then the GUI partitoner as suggested above may be the answer.

---

