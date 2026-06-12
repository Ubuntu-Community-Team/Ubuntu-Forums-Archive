---
title: "root"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-29
how do i switch to root in terminal? ive come across some things that require root but i dont know how to set the terminal

---

### Post by Seisen on 2007-06-29
you can just put "sudo" in front of whatever it is and it will give you temporary superuser rights.

---

### Post by LaRoza on 2007-06-29
Type "sudo" before the command.

Type "gksudo" for graphical apps.

In sudo, you will not be able to see your password as you type, just type it and press enter.

---

### Post by Outrunner on 2007-06-29
use 'sudo' in front of the command, or 'gksudo' for graphical applications, like so
```

gksudo nautilus
```

or ```
sudo aptitude update
```

---

### Post by steve.horsley on 2007-06-29
If you need several commands in root, you can also save some typing by entering the command
**sudo -i **
which raises the root prompt to root privilege. use exit to return  to normal level.

---

### Post by timelord29 on 2007-06-29
i need the root to mount an iso image i downloaded but i cant mount using

mount -o loop -t iso9660 file.iso /mnt/test

i found this on [http://www.tech-recipes.com/linux_tips857.html](http://www.tech-recipes.com/linux_tips857.html) and it wont work when trying to mount my gutsy gibbon tribe 2 iso file. also, i know there is a disk image mounter utility in ubuntu somewhere ( i saw it in the add/remove thing) and i cant find it to reinstall it (something happened where i had to completely reinstall ubuntu)

---

### Post by Outrunner on 2007-06-29
```
sudo mkdir /mnt/test
```


```
sudo mount -o loop -t iso9660 file.iso /mnt/test
```

---

### Post by timelord29 on 2007-06-29
can you tell me how to mount the iso? the code isnt helping much considering i dont know much about using the terminal

---

