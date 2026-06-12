---
title: "several questions"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by lfvo on 2007-04-22
hi people,
i have installed Feisty, and i have some questions.

[LIST=1]
[*]How can a add themes and icons to ubuntu
[*]how can i change the label  ntfs (windows) partition
[/LIST]

to change the label partition i try this
> sudo apt-get install ntfsprogs
> sudo ntfslabel /dev/sda1 newlabel
 and says 
> The device /dev/sda1, is mounted.
Use the force option to work a mounted filesystem.

---

### Post by Happy_Man on 2007-04-22
1. You simply download whatever themes and icons you want, and then go into the SYstem --> Preferences --> Themes and drag and drop! Simple.

2. Try ```
sudo ntfslabel -f /dev/sda1 newlabel
``` and see if that works.

---

### Post by lfvo on 2007-04-22
gives me this errors

> The device /dev/sda1, is mounted.
Forced to continue.
Error opening partition device : Dispositivo ou recurso está ocupado
Failed to startup volume : Dispositivo ou recurso está ocupado
Couldn't mount device '/dev/sda1' : Dispositivo ou recurso está ocupado


---

### Post by Pobega on 2007-04-22
Then unmount it?

umount /dev/sda1

---

### Post by lfvo on 2007-04-22
hi
that dint work, says,
> umount: /dev/sda1 não está montado (de acordo com mtab)

now i have other problem, the icon network/wireless (network-manager) disaper in the bar where is the clock, how can i put it again there?

---

### Post by lfvo on 2007-04-23
> **Pobega said:**
> Then unmount it?

umount /dev/sda1

hi, i made the unmout, then i enter this 
```
sudo ntfslabel -f /dev/sda1 windows
```

then i try do mount with the name /dev/windows and dont work, but if i try with /dev/sda1, work, but the label is the same

---

### Post by Happy_Man on 2007-04-23
Ok, unmount it, then enter: ```
mount /dev/sda1 /media/windows
```

---

