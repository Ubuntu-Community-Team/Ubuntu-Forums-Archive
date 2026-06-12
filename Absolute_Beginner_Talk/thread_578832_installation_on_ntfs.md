---
title: "installation on ntfs"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by cruisinalltheway on 2007-10-17
is it possible to install the OS on an existing NTFS partition?

---

### Post by Pumalite on 2007-10-17
With Vista, use Vista partitioner; free up space, then install. With XP; defrag several times, erase all temp files, then Use Gparted Live CD and 'shrink' XP partition, then install.

---

### Post by santiagoward2000 on 2007-10-17
Not exactly, Ubuntu works on ext3 partitions.

---

### Post by Pumalite on 2007-10-17
The installer does the formatting.

---

### Post by Pumalite on 2007-10-17
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by santiagoward2000 on 2007-10-17
> **santiagoward2000 said:**
> Not exactly, Ubuntu works on ext3 partitions.

Hey Pumalite, I wasn't talking about your post, which is really good. All I was doing was answering the question.

---

### Post by PGHammer on 2007-10-17
> **cruisinalltheway said:**
> is it possible to install the OS on an existing NTFS partition?

Not just on NTFS, but from *within* NTFS (in fact, from *within Windows*).

Some rather bright brains have come up with a variation on Ubuntu 7.04 (Feisty Fawn) called Wubi.  This slick piece of work installs (and uninstalls) on, and within, any Win32 operating system from 2000 up (I see little reason it wouldn't work with NT 4.01, for that matter).  It requires no partitioning or even partition modification.  It even cooperates with at least OS Loader 5 and newer (including OS Loader 6, which is included with Vista).

Yes, it will work with Vista.  (In fact, I'm typing this reply *from* my Wubi Ubuntu installation.)

It's still Ubuntu (I've worked with the standard Feisty Fawn before, and except for the slick install routine, I didn't lose anything, except *not* having to deal with partitioning woes); that means it's still newbie-friendly.  It even updates like any other distribution of Ubuntu (in fact, like Feisty Fawn and later, via the included Update Manager).

However, said slick install/uninstall makes it easily the *scariest* Linux distribution (for some folks) to come down the pike *ever*.

Additional Notes: Synaptic works a treat, too.

---

### Post by cruisinalltheway on 2007-10-17
thanks for all the replies!!

i was asking because i have large files i cant backup on the ntfs, and didn't want to lose them for format. guess ill have to figure out how to move them to another HD.

Thanks again!

---

### Post by Pumalite on 2007-10-17
> **santiagoward2000 said:**
> Hey Pumalite, I wasn't talking about your post, which is really good. All I was doing was answering the question.

Hello: How is Argentina these days. I've been in Bariloche. Great skying. Cheers.

---

### Post by santiagoward2000 on 2007-10-17
> **Pumalite said:**
> Hello: How is Argentina these days. I've been in Bariloche. Great skying. Cheers.

Hmm, quite nice. Last night we had some snow, weird for this time of the year :lolflag:

---

