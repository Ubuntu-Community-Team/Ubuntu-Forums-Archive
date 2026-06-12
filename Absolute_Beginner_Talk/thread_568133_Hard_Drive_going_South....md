---
title: "Hard Drive going South..."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by OldTimeTech on 2007-10-05
My hard drive is starting to make those clicking and grinding noises that hard drives do when they decide it's time to die.  I don't figure this hard drive owes me anything, it's been around for years.

The problem is I've got this hard drive totally setup the way I want it.  If I put a new hard drive in, I have to totally reload.  Is there some way of copying, moving, cloning or something that I can do so I don't lose all my information, settings and such.

I'm using Ubuntu 7.04, any help would be appreciated.

---

### Post by cek on 2007-10-05
You can use the dd command to fully backup one disk to another.

Get the new disk in your system and:

dd if=/dev/hda of=/dev/hdb

I haven't tried this myself, but I assume it will work.  You MAY have to manually partition the new disk, but I don't know about that.

Once you've dd'd it, swap out the disks (so /dev/hdb becomes /dev/hda and the old /dev/hda comes out) and reboot.

However, remember that all of your settings are really kept in your home folder, so just keep a backup of it and reloading would work as well.  (other than additional programs/drivers you've added).

---

### Post by OldTimeTech on 2007-10-05
thanks will check that command out.

---

### Post by indytim on 2007-10-05
Depending upon your partition sizes, you might want to check out Partimage (it's in the repositories).

IndyTim

---

### Post by OldTimeTech on 2007-10-06
Again, Thanks....had not thought about partimage.

Actually have not got around to installing other drive, using my laptop with Ubuntu for the moment, but will get it accomplished sometime this week and will try partimage first and dd second if the partimage does not work.

---

