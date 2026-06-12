---
title: "[SOLVED] ubuntu wont start up"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by cragger on 2008-01-25
i was trying to install some stuff with guides from the interet and gave up. when i restarted the computer it would start to load with the comands then just stops at this(may not be exactly as it was writen as i wrote it down):

0.27200 PCI Bios bug #81 [49435000] found

0.99600 kernel panic  - not syncing: VFS: unable to mount root fson unknown - block (0,0)

---

### Post by MaximusTG on 2008-01-25
Which guide exactly did you follow to do what? Maybe we can backtrace what went wrong from there.

---

### Post by cragger on 2008-01-25
ive looked but cant find the site, the browasing history from firefox would help but i cant login so thats no help, none of thoes numbers or any of that information helps then? i dont no %100 that thats what caused it but the next time i loaded it it wouldnt load

---

### Post by seventhc on 2008-01-25
Did you edit grub at all??
did you enter this into the terminal?
```
sudo gedit /boot/grub/menu.lst
```I just saw this...here is a link
[https://bugs.launchpad.net/ubuntu/+bug/163867](https://bugs.launchpad.net/ubuntu/+bug/163867)
from someone in this post
[http://ubuntuforums.org/showthread.php?t=678141](http://ubuntuforums.org/showthread.php?t=678141)

lol thats you too :P

---

### Post by cragger on 2008-01-25
o lol, ya i was typing the first one up and i thought i closed it, and went to look for it and couldnt find it but i guess it went threw aswell... 

anyways yes i did lookup the bug in launchpad and found that, but like i dont no where to go from there, like should i just reinstall ubuntu or what, and i dont think i typed in that code

---

### Post by cragger on 2008-01-25
about the grub, i did have to type things into the terminal, but it was working fine untill i restarted it

---

### Post by seventhc on 2008-01-25
Can you remember what you typed in the terminal>>??  even if you just guess. :D

---

### Post by cragger on 2008-01-25
no not really, what could have been typed? what was that code?

---

### Post by seventhc on 2008-01-25
That was just the command to allow you to edit grub
sudo allows you to make changes a regular user can't
gedit is a text editor
and /boot/grub/menu.lst is just the path to the file 
menu.lst being the file.

It is really hard to undo anything though without knowing what was done.
You don't even get a boot menu correct?
so no other boot options..
I'm really not to sure what you should do at this point. Even if you boot from the live cd not sure what needs to be done.

---

### Post by cragger on 2008-01-25
o sorry i guess i forgot that detail out, i have a dual boot with vista and the grub loader opens, vista works but when i open ubuntu i get all of that stuff

---

