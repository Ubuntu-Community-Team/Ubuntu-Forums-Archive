---
title: "Mount hard drive from live cd in terminal?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by A-Sylum on 2007-09-18
I need to fix a file in windows but i can't  because i don't have the permissions. so im trying to use the live cd but i cant get the xorg.conf configured correctly. so i need to know how to mount a hard drive and copy that file onto a usb stick in the terminal. any help is appreciated thank you so much for all your help!

---

### Post by moffa on 2007-09-18
You need to first install the NTFS Configuration tool.  Then you have to mount your windows partition to a folder in linux.

xorg.conf configures your display settings, /etc/fstab controls the mount points

After you install the NTFS Config tool (Add/Remove Programs) it should mount it in the /media/[device name] folder.  Your usb stick would be mounted in another folder there too.  Then you just have to copy it over.

---

