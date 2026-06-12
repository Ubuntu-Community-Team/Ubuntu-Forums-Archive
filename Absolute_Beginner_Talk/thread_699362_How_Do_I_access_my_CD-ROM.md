---
title: "How Do I access my CD-ROM"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-02-17
Hi,

I'm running off a really old laptop and I tried installing xubuntu but with no success. Therefore I was forced to use DSL. this has kernel 2.4.31.

I am a 100% novice to the world of linux and I have no idea how to access my CD's. No icon appears and all I seem to have to work with is a file manager. There is a CD-Rom folder but this is on the machine. Can anyone give me a step to step advice on how I can simply copy files from my CD to the HD?? Aaargh I cant even do that, what hope is there??!

---

### Post by zenkaon on 2008-02-17
DSL is an excellent choice for a lightweight Linux distro. I've seen it run on machines with 16MB of RAM!

to access your CDROM you are probably best to open a terminal:

ls /media will show you what fstab thinks it can mount, you'll probably see "cdrom". Then type

mount /media/cdrom (may have to do this with a sudo at the begining, can't remember DSL that well).

Then you should be able to browser the cdrom from a file manager. You can also use the terminal.

remember to unmount if you want your cd back!

umount /media/cdrom
eject /media/cdrom

Hope this helps

---

### Post by -random on 2008-02-17
my cd-rom is unmounted untill i put a cd in, maybe that works for you.

if not, maybe try

mount -t auto /dev/cdrom /media/cdrom

maybe with a sudo in front, also maybe cdrom0 or cdrom1 instead of cdrom.

also, the mount directory must exist. you can make it with 'mkdir /media/cdrom' (also most probably with a sudo).

---

### Post by -random on 2008-02-17
sorry(how do i delete a post?) ;/

---

