---
title: "How do i Install Wine 0.9.3.8"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-14
I downloaded Wine 0.9.3.8 and it's a .tar.bz2 file, I extracted it , adn then what should I do??

---

### Post by waggygee on 2007-06-14
I don't know how to do it that way. But this is how I did it.

Add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

After that, use this command to install.

sudo apt-get install wine

Finally, go to your Update Manager to check if you have the latest Wine release. System -> Administration -> Update Manager

---

### Post by bamesah on 2007-06-14
> **waggygee said:**
> I don't know how to do it that way. But this is how I did it.

Add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

After that, use this command to install.

sudo apt-get install wine

Finally, go to your Update Manager to check if you have the latest Wine release. System -> Administration -> Update Manager

Thanks that worked

---

### Post by skymera on 2007-06-14
i resort to .tar .gz as a last resort, since they require more work.

---

### Post by Amazona aestiva on 2007-06-14
It is so difficult to install Wine.

However here is a way:
See this link: [http://ubuntuforums.org/showthread.php?t=149585]("http://ubuntuforums.org/showthread.php?t=149585")

I advise it, because it is working so well!:D

---

