---
title: "How do i remove a unwanted folder in media"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by jag1475 on 2006-12-20
[FONT="Comic Sans MS"][SIZE="3"][/SIZE][/FONT] how do i remove unwanted folders in my media folder

---

### Post by bodhi.zazen on 2006-12-20
> **jag1475 said:**
> [FONT="Comic Sans MS"][SIZE="3"][/SIZE][/FONT] how do i remove unwanted folders in my media folder

sudo rm -r <folder_name>

---

### Post by jag1475 on 2006-12-20
the folder is in  filesystems /media/ avi1
i need to cd to media  how do i do this

---

### Post by bodhi.zazen on 2006-12-20
to move to the directory use cd:
```
cd /media
```

However you do not need to do this:

```
sudo rm -r /media/<folder_name>
```

---

### Post by jag1475 on 2006-12-20
john@shadow-desktop:~$ sudo rm -r/media/avi1
Password:
rm: invalid option -- /
Try `rm --help' for more information.
john@shadow-desktop:~$  sudo rm -r/media/avi1
rm: invalid option -- /
Try `rm --help' for more information.

---

### Post by jag1475 on 2006-12-20
john@shadow-desktop:~$ cd/media
bash: cd/media: No such file or directory
john@shadow-desktop:~$ cd /filesystems
bash: cd: /filesystems: No such file or directory

---

### Post by bodhi.zazen on 2006-12-20
LOL jag ...

You need a space !
cd<space>/media

Like this:

cd /media

And:

rm<sp>-r<sp>/media/avi1

Like this

sudo rm -r /media/avi1

---

### Post by jag1475 on 2006-12-20
> **bodhi.zazen said:**
> LOL jag ...

You need a space !
cd<space>/media

Like this:

cd /media

And:

rm<sp>-r<sp>/media/avi1

Like this

sudo rm -r /media/avi1
[COLOR="Blue"][/COLOR]****** thanks  it worked

---

