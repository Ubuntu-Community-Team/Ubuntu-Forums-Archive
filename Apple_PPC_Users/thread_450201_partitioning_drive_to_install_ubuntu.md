---
title: "partitioning drive to install ubuntu"
date: 2007-05-21
forum: Apple PPC Users
---

### Post by tr333 on 2007-05-21
Hi,

What is the best way to partition the HDD on my powerbook to install Ubuntu?  Directly from OSX, or ubuntu livecd?

---

### Post by ruy_lopez on 2007-05-21
First you have to disable journaling in OSX disk utility. Then you boot using the live CD and use parted, or gparted to resize your OSX partition. After that when you start the install process for Ubuntu you should be able to claim the free space and set up an ubuntu partition.

see here: [http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by tr333 on 2007-05-21
i tried using gparted/qtparted with a dapper livecd, but it didnt want to resize (maybe the libparted was too old?).  currently downloading the latest gentoo livecd as i have read on the internet that it works for resizing hfs+ :)

---

### Post by ruy_lopez on 2007-05-21
When I did it with the Live CD, at the partitioning stage I had to choose `back`, then `escape to shell` from the list. Then I ran `parted` from the command line.

---

### Post by ruy_lopez on 2007-05-21
I tell a lie. It wasn't the live cd. It was the old ncurses-style install cd. 

While I'm on this topic. The new livecd/installcd might be great for new users, giving them a taste of the OS before they install. But for anyone looking to install the OS, and nothing else, the livecd just gets in the way. There should be an option to bypass the livecd initialisation and head straight to install.

---

