---
title: "change grub.list from a terminal?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mills on 2007-05-08
ok i messed up and put this in my bootlist thing

> /boot/grub/menu.lst
[...]
title Fedora Core (2.6.10) - bootchart
    root (hd0,1)
    kernel /vmlinuz-2.6.10 ro root=/dev/hda1 **init=/sbin/bootchartd**
    initrd /initrd-2.6.10.img

but obviously i messed up, so my question is how do i change boot/grub/menu.lst from terminal as i cant get to any gui's (iam currently in windows)

alex

---

### Post by taurus on 2007-05-08
```
sudo nano -Bw /boot/grub/menu.lst
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by Nythain on 2007-05-08
glad to see im not the only one who prefers nano over pico

---

### Post by mills on 2007-05-08
did the sudo nano -Bw /boot/grub/menu.lst command and got there....but

its a blank screen, i was hoping to actually see the menu.list but instead i think it wants me to write the whole thing from scratch, btw i gotta put the above code in the recovery part cuz the main boot option is no good,

so do i need to write the whole menu.list again?

a reinstall seems easier 2b honest

---

### Post by taurus on 2007-05-08
You didn't boot from the LiveCD, did you?  After you boot into recovery mode from GRUB menu, you don't need to use sudo anymore since you are not logged in as root.

```
nano -Bw /boot/grub/menu.lst
```
And if it is still empty, post the output of this command here then.

```
ls -la /boot/grub
```

---

### Post by mills on 2007-05-08
still the blank screen, heres the results of ls -la /boot/grub

```
drwxr-xr-x 2 root root 4096 may 8 15:47 . 
drwxr-xr-x 3 root root 4096 may 8 15:16 ..
(entries from april here so didnt write them down)
**-rw-r--r-- 1 root root 4996 may 8 15:47 menu.list**
-rw-r--r-- 1 root root 4974 may 7 22:19 menu.list~
(more entries from april here)
```

the highlighted one seems to the one you'd want, 

the helps much appreciated

EDIT; maybe i should say that the text area is blank instead of the screen, it tells me at the top that iam at the menu.list and there are some options listed at the botton of the screen

---

### Post by taurus on 2007-05-08
```
nano -Bw /boot/grub/menu.list
```

p.s.  Not sure why it's menu.list because it should be menu.lst!

---

### Post by mills on 2007-05-08
> **taurus said:**
> ```
nano -Bw /boot/grub/menu.list
```

p.s.  Not sure why it's menu.list because it should be menu.lst!

silly me, i entered list and not lst:oops: 

all sorted now cheers Taurus

---

