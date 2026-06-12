---
title: "Want to make a simple &quot;shortcut&quot; [Resolved]"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by rillip on 2007-04-01
This seems rudimentary, but honestly, Ican't figure it out, so I figured I'd post it here.

I just installed a new driver. I don't want to raid the two together as one's PATA, one's SATA, they have many paritions, one drive is old and I'm worried about failure, etc.

So, what I'd like to do, to make things easy for me, is to have what in Windows would be called a "shortcut" to my new drive.  It's already mounted in /mnt/storage (believe the drive is /dev/sda2), formated as ext3, etc.  All I want to do is have a little graphical icon for when I'm in Konquerer and want to move files from my home folder to the storage drive.  I'm thinking what I want is a symlink.  I'm fairly certain a hard link is inappropriate here.  I can make the link using the right-click menus, easy enough, but I'd like to do it from the command line, just for the experience, but for the life of me I can't phrase my querry well enough to Google the neccesary command.

Thanks in advance.

---

### Post by K.Mandla on 2007-04-01
In general, symlinks from the command terminal are 

```
ln -s /path/to/destination /path/to/link
```

So for example, I have a modular hard drive I mount at /media/modular, and make a symlink to there from my home directory, like this. ...

```
ln -s /media/modular /home/kmandla/modular
```

Does that help?

---

### Post by aysiu on 2007-04-01
Actually, I think if you right-click on the desktop and select *Configure Desktop*, there's an option somewhere in there to show mounted hard drives on your desktop.

---

### Post by rillip on 2007-04-01
K Mandla, that's PERFECT, exactlty what I wanted.

aysiu, thanks for that as well, I had no issues doing that and have done that as well.

---

