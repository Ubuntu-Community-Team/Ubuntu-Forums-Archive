---
title: "Cannot create folder"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by trickyzach on 2008-03-11
I have a external drive (NTFS) that I have hooked up to my ubuntu machine.

Suddenly I cannot create folders.

I get "Unsupported Operation" whenever I try and create a folder.

I can delete/rename files on this drive....


Create folder works on every other drive.

Any ideas?

---

### Post by ferdostar on 2008-03-11
Maybe you have to change the read/write permissions.You can do this by editing your  /etc/fstab file or doing it using NTFS configuration tool. Check [this]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") and [this]("https://help.ubuntu.com/community/FilePermissions") and maybe [this ]("http://www.psychocats.net/ubuntu/mountwindows#mountpoint")

---

### Post by trickyzach on 2008-03-11
Yeah thats what I thought, but it was working fine. Then it just started doing this. I havent unhooked or unmounted the drive either.

Same thing happens after a reboot as well

---

### Post by trickyzach on 2008-03-11
what is also strange is i can cut a folder from the drive and copy it to another folder and it works fine... lol

---

