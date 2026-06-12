---
title: "how to unmount?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-14
i wish to delete my vista partition but when i right click the desktop icon and select unmount i get an error message stating that i dont have the right permissions so i tried

```
sudo umount /media/sda1

```

but all i get is

```
umount: /media/sda1: device is busy
umount: /media/sda1: device is busy

```

could somone help me unmount it please thanx

---

### Post by defrex on 2007-10-14
Are you running anything that's using the drive? Like, say, Nautilus or Rhythmbox?

---

### Post by kamitsukai on 2007-10-14
yer.....you gonna have to help me out here i dont even know what they are let alone that they would use my windows partition :P

---

### Post by Pumalite on 2007-10-14
Try:
sudo umount /dev/sda1

---

### Post by kamitsukai on 2007-10-14
same as before "busy" thanx anyway

---

### Post by qpieus on 2007-10-14
try a force umount```
sudo umount -f /dev/sda1
```

The other option is to run the gparted livecd. It will not mount any of your drives, so you are free to format or do whatever you like to them.

---

### Post by kamitsukai on 2007-10-15
thanx qpieus's worked perfectly now a very happy sole ubuntu user!

---

### Post by qpieus on 2007-10-15
Excellent. Congrats on kicking the windows habit.

---

