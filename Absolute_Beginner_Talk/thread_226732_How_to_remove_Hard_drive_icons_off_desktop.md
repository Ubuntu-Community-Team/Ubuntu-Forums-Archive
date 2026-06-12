---
title: "How to remove Hard drive icons off desktop"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-07-31
Hi

Ive just sucessfully partitioned my new hard drive but the hard drives show on the desktop as well as in the places menu.

I dont want the icons showing on the desktop too.

How do i remove them? :)

Many thanks as always :)

---

### Post by mlind on 2006-07-31
You need to open **gconf-editor** from terminal and untick checkbox located at
/apps/nautilus/desktop/volumes_visible


(or Ctrl+F2 and type gconf-editor)

---

### Post by glinsvad on 2006-07-31
Nevermind browsing gconf-editor, just run this in terminal:
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible false

```

---

### Post by James_N on 2006-07-31
Many thanks to you both. That worked fine :)

---

### Post by brk3 on 2006-11-17
Hi, this worked for me before but Ive just installed edgy and its not working, the icons are still there. any suggestions?

---

### Post by taurus on 2006-11-17
Did you happen to mount it on /media?

---

### Post by brk3 on 2006-11-17
yes!

---

### Post by taurus on 2006-11-17
Then mount it somewhere else like /mnt since everything that is mounted in /media will appear on your desktop.  Therefore, edit your /etc/fstab and change from /media to /mnt and don't forget to create new mount point for your partition...

---

### Post by brk3 on 2006-11-17
Thanks very much :)

---

### Post by taurus on 2006-11-17
> **brk3 said:**
> Thanks very much :)
See how easy it was!!!  ;)

---

### Post by brk3 on 2006-11-17
> **taurus said:**
> See how easy it was!!!  ;)

well in fairness it could be easier, rooting around in the registry just to remove some icons from your desktop seems a bit much for ubuntu's user friendly image dont you think?!

---

### Post by taurus on 2006-11-17
But you also learn how the whole /etc/fstab behaves in Linux instead of click and click and don't understand why it is!!!

---

### Post by brk3 on 2006-11-18
i knew about the fstab thing for ages just didnt know that it mattered where the volumes were mounted! dont get me wrong I dont really care just making a point that your average user doesnt want to know about fstab and these kind of things are enough to send them crying back to windows

---

### Post by EnemyUnknown on 2007-09-10
glinsvad - thanks

---

