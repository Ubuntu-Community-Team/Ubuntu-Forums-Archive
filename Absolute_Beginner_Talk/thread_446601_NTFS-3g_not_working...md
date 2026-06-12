---
title: "NTFS-3g not working.."
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-17
I have installed from the Adept package manager all the bits for ntfs-3g but it does not work.....

ntfs configuration tool appearsin the system menu without an icon and when i click it nothing happens.

typing it in konsole yields

matt@matt-laptop:~$ ntfs-config

** (ntfs-config:5851): WARNING **: Error : This programm need to be run as root.


X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


So if i do sudo su and then ntfs config:

root@matt-laptop:/home/matt# ntfs-config
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(ntfs-config:8063): Gtk-WARNING **: cannot open display:

any help appreciated.

---

### Post by taurus on 2007-05-17
```
**kdesu** ntfs-config
```

---

### Post by gn2 on 2007-05-17
Automatix has an auto-mounter for NTFS and Fat32.

It mounts and makes NTFS and Fat32 writeable automatically on connecting them.

I've used it on my desktop and laptop and it works flawlessly.

Look in the "Miscellaneous" category in Automatix once you've installed it.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by blop on 2007-05-17
Thank you both for your replies...

taurus:- that worked perfectly what bothers me is that i did not have to do that on my desktop(s) that i have installed Feisty on. thanks tho...

gn2:- i have never heard of automatrix but it looks like a perfect program for the noobie that i am!! cheers i will check it out?

are you two anygood with sorting out sound card issues? :)

oh and how do i stop things loading in the back ground for some reason i have HP tool box and VMware running and i dont use them!

---

