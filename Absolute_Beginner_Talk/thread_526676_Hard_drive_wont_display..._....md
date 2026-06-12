---
title: "Hard drive wont display... /??..."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-08-15
umm i dont understand why my sata drive wont display.. it was working not too long ago i think when i ran disk check through windows it might have done something.... please help me out here. i have all my music and stuff on there .  o btw its ntsf drive

---

### Post by meierfra on 2007-08-15
post the output of 

```
sudo fdisk -l
```

```
 mount 
```

and

```
 cat /etc/fstab 
```

---

