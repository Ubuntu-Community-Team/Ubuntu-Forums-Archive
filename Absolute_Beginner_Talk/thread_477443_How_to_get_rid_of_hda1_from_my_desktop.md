---
title: "How to get rid of hda1 from my desktop?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-18
I have dual booted Ubuntu with XP on hda1.  I'd like to still have access to the XP partition via Places but not have it on my desktop.  I've tried rightclicking and 'unmount' but it won't let me.

---

### Post by pmagill on 2007-06-18
Yes I found that quite annoying to begin with but there is a solution...   

Simply hold ALT and press F2 then type gconf-editor then hit enter.

Now in the new window choose "apps > nautilus > desktop" you can now uncheck volumes_visible.
The only problem there is now cds dvds memory pens etc will also not appear on the desktop but only in places or wherever they had been mounted.. Hope this helps

---

### Post by aberadam on 2007-06-18
Thanks.  I kind of like having DVDs/CDs/Pens appearing though!  Is there another solution?

---

### Post by aberadam on 2007-06-18
bump

---

### Post by vanadium on 2007-06-18
Bump after just one hour???

I have posted this alreay several times, but admittedly, it is not always easy to spot the information you need.

You need to mount your hda1 in another place than /media. Everything that is mounted in /media will have an icon on the desktop, which indeed I agree with you is fine for USB sticks, removable devices, etc., but not for a windows partition on a fixed drive. I have a desktop with a Win98 partition (to play tuxracer! Won't work under Ubuntu!) and I moved the mount point to /mnt (which in fact is the "traditional" mount point for external drives)

There are two steps involved: 1) change the mount point in /etc/fstab and 2) create the mount point in your file system (this is in fact just an empty directory).

1) gksudo gedit /etc/fstab
Look for the line of your hda1. In the second entry, change /media to /mnt. Thus, your mount point is going to change from /media/hda1 to /mnt/hda1

2) make a directory hda1 under /mnt. You can do so with a nautilus instance with root rights, but here is how you do it with the command line:

sudo mkdir /mnt/hda1

Upon restarting, the hda1 will be accessible from /mnt/hda1, and won't show up on the desktop anymore. If you are impatient, you can have the changes become in effect right away:

sudo mount -a

---

### Post by aberadam on 2007-06-18
Thanks Vanadium, it's showing as in my "filesystem" now not on the desktop.

---

