---
title: "Can partition size be changed after install?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by UB1KENOBI on 2007-05-25
I am a new to Linux  using Ubuntu 7.04 i386. It seems to be working great; network, wireless and all, but now I would like to repartition the drive to three seperate drives versus one big drive. Is it possible to resize the existing drive and add two other partitions with a Linux utility? Is the Ubuntu 7.04 Install CD the "Live CD" I keep reading about? I've seen commercial products mentioned like Acronis disk director and the old Partition Magic(Now Norton I think).Any advice would be appreciated. I need to set up a dual boot for daughters school work. Thanks. ;)

---

### Post by starcraft.man on 2007-05-26
> **UB1KENOBI said:**
> I am a new to Linux  using Ubuntu 7.04 i386. It seems to be working great; network, wireless and all, but now I would like to repartition the drive to three seperate drives versus one big drive. Is it possible to resize the existing drive and add two other partitions with a Linux utility? Is the Ubuntu 7.04 Install CD the "Live CD" I keep reading about? I've seen commercial products mentioned like Acronis disk director and the old Partition Magic(Now Norton I think).Any advice would be appreciated. I need to set up a dual boot for daughters school work. Thanks. ;)

This [guide]("http://www.psychocats.net/ubuntu/separatehome") is a very good explaination, its for making a home directory after installed but should be easily translated to two extra partitions.

I prefer using the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). I have acronis disk director, I stopped using it... I prefer gparted I think, its easy and OSS. 

I would of course back up any vital data, no partition editing operation is without risk, I don't wanna be responsible if you delete something important >.>.

Hope it goes well.

Edit: Oh and... *turns really dark and evil* prepare to DIEEEE JeDIIIII!!!! *fries him with force lightning* Gotcha when ya wasn't looking :p

---

### Post by Nikron on 2007-05-26
Yeah, you can like UB1KENOBI said.  I'll toss a vote for gparted, very easy to use, and worked excellently.  And of course back up your data.

---

### Post by UB1KENOBI on 2007-05-26
Thank you. I'll try it. Thanks for the links too.

---

### Post by starcraft.man on 2007-05-26
> **UB1KENOBI said:**
> Thank you. I'll try it. Thanks for the links too.

HA! Typical Jedi, always nice and soft after fried with electricity :p

Have fun and let the dark side take you, young one :D.

---

### Post by bluknight on 2007-05-26
Just be v careful if your /etc/fstab file contains UUIDs because partition size changes UUIDs too.
Read about it here regarding /home partition
[http://ubuntuforums.org/showthread.php?t=454339](http://ubuntuforums.org/showthread.php?t=454339)

---

