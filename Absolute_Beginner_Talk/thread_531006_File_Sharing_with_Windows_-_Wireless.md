---
title: "File Sharing with Windows - Wireless"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-21
I am wondering how I would share files with a windows XP PC.

I have an ubuntu laptop connected wirelessly to a router (netgear) and from the router, an ethernet cable to the XP PC.

I have enabled file sharing on Windows and it is connected to MSHOME. I enabled shared folders (SMB) and can see the PC on my laptop and vice versa, but they cannot read files from eachother. On the PC when I try to connect to "Fraser-laptop" it requests a username and password and when, on the laptop, I try to connect to "Homepc" it show no files even though on XP shared docs has a hand beneath it (to show it's shared.) When I had windows on my laptop it worked perfectly (unlike anything else.)

Thanks, Fraser

---

### Post by mikeyphi on 2007-08-21
You need to install a small program in windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
this will let you 'see' your Linux files under windows

You need to install ntfs-3g, using synaptic, to read/write to windows

---

### Post by hyper_ch on 2007-08-21
well, when you want to connect from your PC to your laptop enter your laptop's username and password in it. That should authenticate you as user on the laptop and you should gain access.

---

### Post by louieb on 2007-08-21
I just set up samba using this [HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605")
Took about 30 min. works like a champ.

---

