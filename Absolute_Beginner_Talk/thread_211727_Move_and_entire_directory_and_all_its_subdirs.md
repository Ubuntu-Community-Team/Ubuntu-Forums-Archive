---
title: "Move and entire directory and all its subdirs"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Dazaablack on 2006-07-08
Hi I have been reading the mv man, But I cant quite work out how to do this.

I also need to move the files to a directory which you need root permissions to write to. I would normally do this via X but I dont have root permissions. and I dont know how to su.

so I am guessing a command i need will be something like,

sudo mv (dir) (options) (destination dir)

I also want my command line to take care of subdirs.

any help is appreciated.

---

### Post by scxtt on 2006-07-08
if you move a directory that has subdirectories, it moves the subdirectories as well ...

[indent]sudo mv /home/dazaablack/MoveDir /etc/codecs[/indent]

will give you /etc/codecs/MoveDir and any directories/files that are in MoveDir ...

---

### Post by aysiu on 2006-07-08
You don't have to do this with the command-line if you don't want to.

Just press Alt-F2. This will open a **Run** dialogue.

In that dialogue, type ```
gksudo nautilus
``` for Gnome or ```
kdesu konqueror
``` for KDE. Now you're browsing as root.

---

