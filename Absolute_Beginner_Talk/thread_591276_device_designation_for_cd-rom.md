---
title: "device designation for cd-rom"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by jazzybob on 2007-10-25
How can I elicit the designation of my CD-drive?  It's the only IDE device on the computer.  It there a utility that will find the designations for each device (i.e. ubs prots, CD rom, etc.)?

---

### Post by p_quarles on 2007-10-27
You can always type this in the terminal:
```
sudo lshw
```
This will give you the device names of every registered piece of hardware on the system. Keep in mind, though, that any device containing a filesystem will have a mount directory different from its device directory. If you have a default setup, the CD drive would mount in the /media directory, and you can get its exact name by typing:
```
ls /media
```

---

