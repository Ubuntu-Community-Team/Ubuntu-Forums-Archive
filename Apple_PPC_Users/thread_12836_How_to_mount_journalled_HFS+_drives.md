---
title: "How to mount journalled HFS+ drives?"
date: 2005-01-27
forum: Apple PPC Users
---

### Post by adamw on 2005-01-27
Is this doable?  I can't seem to get it to work with the usual
sudo hpmount -r /dev/hda3 /mnt/mac
(I get the error: hpmount: /dev/hda3: This is not a HFS+ volume (Unknown error 4294967295)

---

### Post by lubod on 2005-01-27
Not sure what hpmount is (gotta read the man page!) but I would do:

mount -t hfsplus /dev/hdxx /mnt/mac
(temporary, until next reboot)

or edit /etc/fstab with similar info to make permanent.

does journalling change the process?

if so both the mount command and fstab have optional switches for read only, so nothing is altered.

---

### Post by adamw on 2005-02-02
Thanks, that did the trick.

---

### Post by chascon on 2005-02-16
I can mount the HFS+ partition.  But I can't read file as they "seem" to belong to someone else.  I believe I can circumvent this problem by chaging gid/uid but can someone elaborate on how to do this?

And no, I couldn't figure out any flags to help out with this as recommended elsewhere (It was hinted at, not explained elsewhere).

update:
some of these permssions problems can be solved simply by creating a folder to mount OS X within ~.
For instance,
sudo mount -t hfsplus /dev/hda3 /home/mauro/macOSX

Then you can drag and drop to Shared on OS X, but users still show up restricted.
Nice backup utility though.

And no this is not permanent to next reboot as simply reruning the command with "umount" rather than "mount" unmounts OS X.  Such as in,
sudo umount -t hfsplus /dev/hda3 /home/mauro/macOSX

---

### Post by ewaldgroup on 2005-03-04
Has anyone looked at this? Does it solve the problems we've been having? It doesn't look like it, but for someone new it makes a good tutorial.

[http://www.yellowdoglinux.com/support/solutions/ydl_4.0/hfsplus.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_4.0/hfsplus.shtml)

-ewaldgroup

---

### Post by skipunk on 2005-03-11
I have tried using both the instructions posted early in the thread and the yellowdog instructions, but nothing seems to work.  It executes the command, but nothing gets mounted.  Does it matter that I am just using the liveCD?

---

