---
title: "Playstation 3 Resolution"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by BlueOctober on 2007-11-03
I'm sorry if this topic has been made a 1,000 times. I'm really lost and have tried almost everything.

I have tried this

message=/etc/kboot.msg 
default=linux 
timeout=10 
linux_old='/boot/vmlinux.old initrd=/boot/initrd.img.old root=/dev/sda1 video=ps3fb:mode:' 
linux='/boot/vmlinux initrd=/boot/initrd.img root=/dev/ps3da1 video=ps3fb:mode:' 

but the file is read only and I can't change it under properties.

I could pull my hair out right now.

---

### Post by gn2 on 2007-11-03
Welcome to the Ubuntu forums.

There's a bit about the PS3 in the 7.10 release notes which may help:

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

### Post by Sirhanz on 2008-04-04
You must have root priveledges to edit the file. type sudo before any command and you will be prompted for your password to initiate the command. So in your case type sudo nano or sudo gedit then the file you want to edit. You do all of this in the terminal. So something like sudo nano /etc/kboot or whatever the name is of the file you would like to edit. after editing press ctrl x to save, hit y for yes, then accept the default filename to write it.

---

