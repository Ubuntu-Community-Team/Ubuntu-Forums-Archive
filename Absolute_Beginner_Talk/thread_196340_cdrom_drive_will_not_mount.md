---
title: "cdrom drive will not mount"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Drifter on 2006-06-14
how do you find what the cdrom is called and then how do u mount it.  I can play a dvd because it automatically opens in xzine.  I have installed quicken with wine it works but I can't get it to back up my file.  can someone help with this, if you know of a how to just point me there and I will try.  I have looked very long and hard for a solution to this.

---

### Post by Joeb on 2006-06-14
Normally to mount the cdrom you would just pop it in the drive and it would mount automatically.  However, if that isn't happening, to manually mount it, from the command line (in a terminal window) type:

mount /media/cdrom


If it gives an error about only root can mount it, then type instead:

sudo mount /mendia/cdrom


However, if you are trying to mount a music cd, you should be aware, that you can't actually do that.  Only data cds can be mounted.  For music cds, you would just open up one of the music players to play the cd.

---

