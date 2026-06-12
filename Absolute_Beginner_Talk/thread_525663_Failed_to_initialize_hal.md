---
title: "Failed to initialize hal"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Hughsy on 2007-08-14
Hey, 
Ive been getting the above message every time I log on. Attached is a screeny. I searched the forum and tried the solutions but they didnt work. Any help is, as always, gratefully appreciated.

---

### Post by Jimmyfj on 2007-08-14
I've had that message a few times installing 7.10 Tribe 4. It took 3 attempts before the system started Live Cd without that error. Seems like some error in installation.

You could try: "dpkg-configure -a"  - but I would just reinstall the system since there's obviously some error in HAL.

---

### Post by Hughsy on 2007-08-14
uuugghh nightmare. I just had everything configured as well. Oh well, reinstall it is.

---

### Post by silent1643 on 2007-08-19
> **Hughsy said:**
> Hey, 
Ive been getting the above message every time I log on. Attached is a screeny. I searched the forum and tried the solutions but they didnt work. Any help is, as always, gratefully appreciated.

you shouldn't need to reinstall ubuntu.

try reinstalling the HAL packages from synap

---

### Post by Hughsy on 2007-08-20
reinstalling HAL didnt help. Had to reinstall, and the same thing happened again. Ive a feeling its to do with automatix. I might leave that alone and just install everything manually myself

---

### Post by jfernyhough on 2007-08-21
It's not Automatix (though I've no idea why on Earth you would want to use that :P ) I've got the exact same error on my Tribe 4; it's not an error that always pops up. Some boots work perfectly, others do not.

---

### Post by jfernyhough on 2007-08-21
And in fact I just did a

sudo aptitude reinstall hal

Which stopped, reinstalled and started HAL perfectly.

---

### Post by jmoorse on 2007-11-12
I had this same problem, changing the CONCURRENCY variable from 'shell' to 'none' in 

 /etc/init.d/rc

Fixed the problem

---

