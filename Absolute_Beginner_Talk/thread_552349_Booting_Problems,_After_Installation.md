---
title: "Booting Problems, After Installation"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Kamaki on 2007-09-16
I recently installed Ubuntu without any problems and was able to run it from the GRUB Bootloader without any problems.
Now however, whenever I try to run Ubuntu it always ends up with this error:

CRC Error
Kernel panic - not syncing : VFS : unable to mount root fs on unknown - block (0,0)

Little extra bits of info are that I only booted into Ubuntu once succesfully after install. I didn't change anything so I don't think anything I did within Ubuntu is causing this error... of course I'm a begginer so what do I know.

Help if possible please?

---

### Post by limbourg31 on 2007-09-16
it seems that the kernel is not being associated with the file system, basically stuff doesn't seem to be integrating. possibly its corrupted on some blocks. if there isn't any major info on that partition, i would reccomend you just delete the parition and re-install ubuntu, since that's only a twenty minute process.

---

### Post by Kamaki on 2007-09-16
Ubuntu is on its own seperate drive, I did this specially for Ubuntu :P I will try re-installing it though. I'l reply with the results later.

---

