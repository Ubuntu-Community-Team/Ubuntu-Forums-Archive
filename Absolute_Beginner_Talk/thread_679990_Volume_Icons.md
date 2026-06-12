---
title: "Volume Icons"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Lvcoyote on 2008-01-27
Is there a way to remove the volume icon when I open the computer window??  In particular I want to keep the "153.4 GB Volume" from showing.

Thanks!

---

### Post by barrack on 2008-01-27
There are a couples ways you can go about it.

1- Rename your drive, if all you want is not to show the size of the volume.

2- Not have that volume automount, if you don't often use that partition. I had to do this when I dual-booted and the windows partition would always show up.

3- This link is helpful if you actually want not to see the icons at all.

[http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/]("http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/")

---

### Post by Lvcoyote on 2008-01-27
The 153.4 GB Volume is actually a raid0 array that houses WinXP and it cant be mounted anyway by Ubuntu 7.10, so I just as well make it not even show.  I'll try the link you provided.

---

### Post by Lvcoyote on 2008-01-27
The link provided did not have the solution.  So how do I keep it from auto mounting??

---

### Post by Lvcoyote on 2008-01-27
I'm trying to get the whole icon from showing at all.

---

### Post by philinux on 2008-01-27
Put a hash in front of the line for it in /etc/fstab

sudo gedit /etc/fstab

[edit] sorry this just stops the volume being mounted and appearing on the desktop.

---

### Post by Lvcoyote on 2008-01-29
Thanks phil for the effort, but I'm trying to find a way to stop in from showing in the "My Computer" window when I open it up.

The way my system is set up is as follows:
2X WD120gb in raid0 (housing windows vista X64)
2X Hitachi 80gb in Raid0 (housing Windows XPSP2)
1X Hitachi 80gb (housing Ubuntu 7.10)
1X Seagate 80gb (used for storage only)

The volume housing Vista does not show in the window but the volume housing XPSP2 does, there must be a way to stop it from showing.....

Thanks again!

---

