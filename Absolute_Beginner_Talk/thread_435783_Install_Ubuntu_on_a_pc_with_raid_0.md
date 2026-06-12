---
title: "Install Ubuntu on a pc with raid 0"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by tenth on 2007-05-07
Hello all, I have finally decided to get into linux.
I have been looking over alot of info but I can not find an answer to my problem.
I run windows xp on a pc with 2 160G hard drives in raid 0 (nvidia nforce4 chipset).
I would like to set up a duel boot system and keep all my existing data.
I can not seem to find an easy way to do this :(
Any info you guys can give to me will be greatly appreciated.

---

### Post by MikeEvans on 2007-05-07
If its hardware RAID it should be transparent to the OS. Did you try booting from the Ubuntu CD and viewing partition information?  If you can see volumes and partitions you should be good to go.  Now I have never attempted this myself, maybe someone with experience can back me up.  You could try making a backup image of your data before installing so you have a failsafe.

---

### Post by fakie_flip on 2007-05-07
If you want a Linux software raid, install Ubuntu Server because its installer has support for raid, then you do apt-get install ubuntu-desktop to get Gnome.

[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by tenth on 2007-05-08
I am actually running a fakeraid. I would not mind using my 2 hard drives separately  but I don't want to lose my data because I plan on duel booting. I also have an external drive that I can backup windows to if that would help.

Any Ideas?

---

