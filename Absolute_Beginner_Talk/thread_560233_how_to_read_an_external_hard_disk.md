---
title: "how to read an external hard disk"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2007-09-26
Hello guys
Yesterday i bought a new hard disk that I discover is a ntfs partition. How can I convert it in a read- write hard disk? thank you very much

---

### Post by jw5801 on 2007-09-26
If you're only using it for Linux, then you can reformat it to ext3 using the partitioning program of your choice. I personally use GParted.
```
sudo apt-get install gparted
```

---

### Post by antonio_ing on 2007-09-26
i have installed gparted and run it in the terminal, but it give me an error. Maybe i wrong something when i select the options?

---

### Post by jw5801 on 2007-09-26
I don't see an error there... what happens when you try to make the partition?

---

### Post by antonio_ing on 2007-09-26
everything seems to be ok. I restarted my system and now it works nice. Thank you jw5801

---

### Post by antonio_ing on 2007-09-26
But now isee another problem. How can I eject the hd? because each time that i eject it by the interface, it start the process to be mounted again

---

### Post by jw5801 on 2007-09-26
Sorry, had to go out for a second. Which interface are you unmounting (ejecting) it in? Gnome? Or from within GParted. Either way run this command in a terminal first: ```
sudo killall gnome-volume-manager
```That's the process that automounts partitions, so killing it will stop that from happening.

---

