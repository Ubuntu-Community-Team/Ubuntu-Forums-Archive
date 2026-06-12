---
title: "Mounting Windows partition with LiveCD"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by RepoOne on 2007-01-14
Alright, I am using the livecd of Ubuntu 6.10, and I would like to be able to access my windows files without messing with them, for I don't want to try anything with installing linux yet until I have all my windows files backed up. How do I mount my C: drive so I can get to my music and programs and stuff?

---

### Post by mykalreborn on 2007-01-14
you enter the terminal and type:
```

sudo mkdir /mnt/win
sudo mount /dev/hda1 /mnt/win

```
and then you're set. you should know though, you'll probably not be able to listen to your music tracks and you'll definetly not be able to use your programs.

---

### Post by jd65pl on 2007-01-14
You will require codecs for the media you wish to play. I know NTFS writing has been a gray area in the past not sure right now but its probably best if you don't try writing to your NTFS partition

---

### Post by RepoOne on 2007-01-14
The folder can not be displayed. You do not have the nessecary permissions to view the contents of "win".

---

### Post by mykalreborn on 2007-01-14
> The folder can not be displayed. You do not have the nessecary permissions to view the contents of "win".

try this in the terminal:
```

sudo nautilus /mnt/win

```

---

### Post by jd65pl on 2007-01-14
Giving root access to a graphical program can be risky, you could experience difficulties with file permissions in the future. Instead of using 'sudo' which should only be used with command line programs use 'gksudo' if you really have to have root access to a graphical interface.
```

gksudo nautilus /pathName
```

---

### Post by mykalreborn on 2007-01-14
> **jd65pl said:**
> Giving root access to a graphical program can be risky, you could experience difficulties with file permissions in the future. Instead of using 'sudo' which should only be used with command line programs use 'gksudo' if you really have to have root access to a graphical interface.
```

gksudo nautilus /pathName
```

good to know dude! thanks! :D

---

