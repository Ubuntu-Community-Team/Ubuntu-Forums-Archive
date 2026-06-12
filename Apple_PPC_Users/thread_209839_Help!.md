---
title: "Help!"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by jdhladky on 2006-07-05
first of all, i love Ubuntu, and i installed it to dual-boot with OSx and it works fine, except for one little problem:
I want to set osx as he default os, but i cant. 
I follow the instructions in the desktop guide but when i try to back up the menu.lst file "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup" i get this error: "cp: cannot stat `/boot/grub/menu.lst': No such file or directory"
I just want to change my defualt os to osx. 
I am running 6.06 on a powerbook G4.

Please, help!

---

### Post by taurus on 2006-07-05
Maybe you use LILO as your boot manager!!!  See if you have /etc/lilo.conf...
```

more /etc/lilo.conf

```
Otherwise, what is the output of this command then?
```

ls -la /boot/grub

```

---

### Post by jdhladky on 2006-07-05
/etc/lilo.conf: No such file or directory

and the output of the other code was : ls: /boot/grub: No such file or directory


What does this mean???

---

### Post by tidris on 2006-07-05
You have a G4, so the bootloader is yaboot. Look for /etc/yaboot.conf. Try man yaboot.conf for info on how to edit that file.

---

### Post by jdhladky on 2006-07-05
Great, i have yaboot.conf up but how do i edit it to make mac osx the default?

Sorry, im new at this and used to the overly simplified mac os x

---

### Post by linear on 2006-07-05
Dead simple. Add the line:

**defaultos=macosx**

Save yaboot.conf, and then run:

**sudo ybin -v**

---

### Post by jdhladky on 2006-07-06
YAY!!!

I't worked!

So thanks for picking up where the Ubuntu Desktop guide left off. 
:D

---

