---
title: "Migrate Dapper to a larger hard dirve?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2006-12-09
I have been messing with linux for a year or two, with the help of all of you on this forum (thank you).  I have Ubuntu Dapper 6.06 about where I want it (configuration wise) --however I find my self getting short of hard drive capacity.  I want to install a larger hard drive and (hopefully) migrate my Ubuntu installation to it from the smaller 20 gb drive.Is there a way to do this without going through a complete reinstall and keep my /home directory intact? 

The aim here is to run a few windows programs using VMware which I have installed and gotten operational. Eventually I want to wean myself away from Windows, but for now, this isn't in the cards. I have windows XP Home installed on my first hard drive (hda 30 gb).

---

### Post by aysiu on 2006-12-09
Use PartImage:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by kinematic on 2006-12-09
you can use partimage to make an image of the root partition and plunk it on the new drive.
then edit fstab and grub so they correspond to the new setup....reboot and it should work i think(maybe :-k  )

---

### Post by smoker on 2006-12-09
the easiest way to do this is visit the manufacturer of your new drive's website and download their ultility for copying all the data from the old to the new drive,

---

