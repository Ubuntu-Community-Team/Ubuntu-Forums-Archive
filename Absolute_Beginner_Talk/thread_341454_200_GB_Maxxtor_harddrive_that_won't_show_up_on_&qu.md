---
title: "200 GB Maxxtor harddrive that won't show up on &quot;My Computer&quot;"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Galactic Jack on 2007-01-18
Plain and simple, I have a 200GB Maxxtor HD that won't show up on "my computer" I has been recently formatted from NTFS to ext3 via Gparted and prior to the repartitioning it was showing up as a disk drive.

I have it successfully mounted in my /mnt folder, so it works fine and I can transfer data on and off of it, I just want it to show up as a disk icon in "My Computer"

Any suggestions as to how to get it back like this?

GJ

---

### Post by ljpm on 2007-01-18
"My Computer" as in Windoze can't read it?
or "Computer" as in Ubuntu can't read it?

---

### Post by Galactic Jack on 2007-01-18
Ubuntu is the only OS I am running. I cleared Windows ;)

---

### Post by zerhacke on 2007-01-18
There is no "My Computer" on Ubuntu.

However, if you were to mount it in the /media folder it will automatically symlink to the Desktop, putting an icon on the desktop you can use to get to your data.

---

### Post by Galactic Jack on 2007-01-18
Ahh sweet. Didn't know that. I'll try it out and see how it goes.

Thanks for the tip!

[And you're right, there is no "My Computer" so I'm glad you understood it as the equivalent]

GJ

---

