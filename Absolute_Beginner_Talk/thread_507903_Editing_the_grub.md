---
title: "Editing the grub"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by m10sang10 on 2007-07-23
Greetings, gentlemen: My PC has two HDs-both Sata. In one of them, I've got Ubuntu and XP Professional as OS; both are working fine. Obvously, the boot is grub. The other HD, which I'm just going to add to the computer, has Windows XP home. I want to add this one to grub as well. Alas, but it is unknown to me how to do so. I would truly appreciate if you tell me how.

---

### Post by asmoore82 on 2007-07-23
you must edit the file '/boot/grub/menu.lst' with root priviledges ... and back it up first ...

open a terminal and ...

```
~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
~$ sudo gedit /boot/grub/menu.lst

```

now... add these lines to the end of that file ...

```

## Windows XP Home on the 'other' hard drive
# Added by *yourname* on Monday, 2007-07-23
title Windows XP Home
rootnoverify (hd1)
makeactive
chainloader +1
```

---

### Post by m10sang10 on 2007-07-23
Thank you Asmooree, I ask you a last question; what is the best way to make the Backup? (for example to a floopy disk?).
Thanks again

---

### Post by asmoore82 on 2007-07-23
> **m10sang10 said:**
> Thank you Asmooree, I ask you a last question; what is the best way to make the Backup? (for example to a floopy disk?).
Thanks again

that first command at the term makes a backup ....
```
~$ cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
==
COPY from FILE to ANOTHER FILE

=D

---

### Post by m10sang10 on 2007-07-23
You are incredibles! , thanks a lot.

---

