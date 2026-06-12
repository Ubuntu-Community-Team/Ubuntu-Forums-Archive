---
title: "removable disk drive with no executable permission"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-04-30
ok, so i have a removable hard drive, and when i plug it in, a window pops up asking me to do whatever (ie. open in konqueror, play music with amarok, etc..) so i open in konqueror so the disk mounts.  

to try and keep it simple, how do i mount the drive with executable permission?  i go into the "Disk and Filesystems" link in the system settings, it says it has some weird mount point in /proc.  i can write and read perfectly fine.  

if i should post some file i would, but i have no idea what to post.  i though fstab, but i guess that is for more permanent disks.

---

### Post by starcraft.man on 2007-04-30
I'm no expert on mounting and unmounting drives, but I'm fairly sure you want to mount that in the media folder so that it reads /media/USBDrive. Thats where I believe all your CD DVD and HDDs should be. You should probably read through the [UbuntuGuide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") sections for mounting drives.

Check the index for your exact situation.

---

### Post by rbprogrammer on 2007-04-30
well yea, thats where i always mount it, at [ /media/disk/ ].  but for some reason in the system settings, it is mounted at [ /proc ].  so i dont want to mess with that.  but i want to be able to change my mount permissions for that disk.

---

