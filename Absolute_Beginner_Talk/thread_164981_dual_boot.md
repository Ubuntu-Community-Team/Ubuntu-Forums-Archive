---
title: "dual boot"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by brihy1 on 2006-04-23
i installed ubuntu on a seperate partition with xp pro,how do i get xp pro to default boot?

---

### Post by henryk69 on 2006-04-23
Edit the file /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```
find the **"default"** section and change the number from 0 to 1 (I persume you have only ubuntu and windows sytems installed - if not attach the file)

---

### Post by Nikusan on 2006-04-23
[QUOTE=henryk69]Edit the file /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```
find the **"default"** section and change the number from 0 to 1 (I persume you have only ubuntu and windows sytems installed - if not attach the file)[/QUOTE]

You might have to change the number to something more like 4, from memory. If you had *ubuntu, ubuntu(recovery mode), memtest, "other operating systems" and windows* in your grub list, you would need to default to be 4.

---

### Post by MHlavsa on 2006-04-24
You beat me to it, I was just going to say that.  I blindly changed it to 1 and got recovery mode.  For me it was 4 also.

---

### Post by brihy1 on 2006-12-11
thanks a lot guys,it worked

---

