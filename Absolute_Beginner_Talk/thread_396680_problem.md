---
title: "problem"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-29
hi there

i tried to mount a partition like that 

mount /dev/hdc3 /home/muhammad/Desktop/


then after i did that ,all the icons which were on the desktop disappeared more over that 

a folder with that name appeared lost+found which isn't accessible from the gui 


also when i try to make a new txt  and save it to the desktop , it told me that nothing can be written

so i want to restore my default desktop with it's icons and the ability to save files on it 

and please tell me the command to remove that directory from my desktop

---

### Post by solar george on 2007-03-29
> mount /dev/hdc3 /home/muhammad/Desktop/

```
sudo umount /dev/hdc3
```

---

### Post by ceezax on 2007-03-29
ok 

then what about that problem that i can't write to the desktop ???

i want to be able to save files to the desktop

---

### Post by solar george on 2007-03-29
Try rebooting.

---

### Post by solar george on 2007-03-29
The follow up post is at [http://www.ubuntuforums.org/showthread.php?t=396690]("http://www.ubuntuforums.org/showthread.php?t=396690")

---

