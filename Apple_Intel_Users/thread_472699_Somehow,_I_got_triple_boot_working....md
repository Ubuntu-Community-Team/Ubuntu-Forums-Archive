---
title: "Somehow, I got triple boot working..."
date: 2007-06-13
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-13
I'm not sure how it's working, as I didn't do half the stuff in the guides.

All I did was:

1. Create partitions with diskutil
2. Install  rEFIt
3. Install XP from CD
4. Install Apple's Window drivers
5. Install Ubuntu from CD using GUI interface (not terminal)

Obviously, I had to reboot after every step above.

I did try to manually mount the Linux partition in the terminal, but got an error. So in the end, I just skipped all the terminal commands and did a straight install using the GUI installer.... I formatted the partition as ext3 and created a 512 MB swap file with the leftover space.

I did NOT install lilo, and Grub seems to have installed fine. Is this normal?

---

### Post by Greywhind on 2007-06-13
Grub has been fixed for Intel Macs in Feisty. Yes, it's now normal not to have to install Lilo.

---

### Post by Torajima on 2007-06-13
> **Greywhind said:**
> Grub has been fixed for Intel Macs in Feisty. Yes, it's now normal not to have to install Lilo.

Okay, thanks. This makes triple booting a lot less daunting... hopefully someone will create a new guide that leaves out all the unnecessary bits.

---

