---
title: "Windows partition won't auto-mount"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by michael.dobrofsky on 2007-08-27
Hi All,

I'm a newbie Ubuntu user, long-time Windows user. I recently installed Ubuntu and played around with it to see if it could replace Windows. Well, I really liked it and played around with apps and settings and what not.

Anyways, the first time I installed Ubunutu, I could mount my Windows partition by double-clicking on the drive icon in the browser. It would mount no problems and just appear and I could browse it.

Since then, I've reinstalled Ubuntu because I kinda screwed up the first installation whilst exploring and playing around, so I wanted to start fresh and from scratch again. But now, on reinstall, I can only mount my Windows partition by using sudo mount /media/sda1. It won't let me double-click and mount. I get a permission denied error as it's owned by 'root'. I never had this on my first installation? I figure I've done something wrong with the partitioning on install?

Can anyone please help a newbie. I'd really appreciate it.

Cheers,

Michael.

---

### Post by wolfen69 on 2007-08-27
in terminal:
```
sudo apt-get install ntfs-config
```
it will show up in applications>system tools

---

### Post by michael.dobrofsky on 2007-08-27
Thanks, but that didn't seem to solve anything? It did add the little app helper in the Sys Tools, but I still can't mount/umount automatically, and what's more the main problem I'm having is that I can't see the Windows partition in Applications, i.e. Google Picasa, when I want to add photos from that partition. Even though the partition is mounted, it's not showing up in Picasa, but on my previous Ubuntu install, it was.

I fear I've screwed up the partitioning somehow on install, but am not sure what I did?

---

### Post by bme on 2007-08-27
please post your /etc/fstab file

---

