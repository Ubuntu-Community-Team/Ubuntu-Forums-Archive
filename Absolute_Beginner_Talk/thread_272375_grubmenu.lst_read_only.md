---
title: "grub/menu.lst read only"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by old_dog on 2006-10-06
Installed ubuntu two days ago trying to change the boot sequence in boot/grub/menu.lst using vi. read only! tried chmod to change it, not allowed. At command line entered su and my normal password not accepted. I did not set a super user password during install.
I feel I missed something along the way.

Be good Mike

---

### Post by petri on 2006-10-06
You have to use **sudo** instead of **su**

like

```
sudo nano /boot/grub/menu.lst
``` hit Enter and then password.

or

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Kateikyoushi on 2006-10-06
Try to edit it with 

```
sudo vi menu.lst
```

---

### Post by Jagot on 2006-10-06
```
sudo vi /boot/grub/menu.lst
```

---

### Post by geezerone on 2006-10-06
Argh not the dreaded vi!! lol

---

### Post by old_dog on 2006-10-06
Thanks people....
New Tricks and all that

---

### Post by Aberrix on 2006-10-06
> **geezerone said:**
> Argh not the dreaded vi!! lol

vi for teh win.

---

### Post by tonyr1988 on 2006-10-06
/me seconds

---

### Post by Naegling23 on 2006-10-06
Ive never used gnome, but if your running kde, you can right click on the file and edit as root.  Apparently there is a plugin for nautalis that will enable you to do this as well.  Its much easier than using the console.

---

### Post by nale on 2006-10-06
:)

---

