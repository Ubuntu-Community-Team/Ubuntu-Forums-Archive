---
title: "Pseudo-Noob with drive selection question"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by CRJeepin on 2007-10-19
Hey all,
First off, thanks for what looks to be a great forum.  Have read a couple of the HOWTO's and there's some great information on here!  I'm an old RedHat user, been a *long* time (8+ years) since I ran Linux at all but I was able to stumble my way around OK and even wrote a couple small apps.  However, I got away from it after college and really haven't looked at it again!

BUT I'm jumping back in and want to dual-boot Ubuntu with Windows XP, and am hoping someone can refresh my memory on what the best way to use my drives would be.  Right now, I've got:

1) 250 GB SATA (XP boot drive, one big partition currently).  Using about 100 GB.

2) 80 GB IDE (empty)

3) 40 GB IDE (full w/backup files)

What I'd **like** to do is use the 80 GB drive exclusively for Ubuntu, splitting it into 2 partitions (one being for RAM/scratch of approx 2 gb, the other being the rest of the drive for the main install).

Anybody see any problems with doing this?  From what I recall, Linux shouldn't care what drive it lives on as long as the Boot Loader is on the boot drive, right?

Any recommendations for the install are appreciated, have downloaded and burned the 7.10 CD already and want to give it a shot tonight.

Thanks!
CR

---

### Post by Hobo Joe on 2007-10-19
I've never booted with separate drives before, but you should just be able select that drive in the installer, and partition it how you want and set it at root.

I'd say go for it, with something like this, messing around with it won't damage your Windows install.

---

### Post by CRJeepin on 2007-10-19
Well, tried that and it installed fine without disrupting my windows install, but I don't think I parked the boot loader on the right drive.  It asked where to install the boot loader and I left it at the default setting, which I believe was "hd0", but that doesn't make sense....I have three drives, XP boots from hd3. 

Re-running installation now but oddly enough, it hasn't asked me yet where to install the boot loader....we'll see.

---

