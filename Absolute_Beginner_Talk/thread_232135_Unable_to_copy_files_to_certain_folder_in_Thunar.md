---
title: "Unable to copy files to certain folder in Thunar"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jis on 2006-08-08
How can you do such file management operations that need "sudo" when done in command line?

---

### Post by dmizer on 2006-08-08
i highly suggest sticking to the command line when performing tasks which require root access.  you can mess up your entire system with a miss click.

is there something that's causing you problems trying to accomplish in the terminal which you could otherwise do with thunar?

---

### Post by anaconda on 2006-08-08
type

gksudo nautilus

in terminal. And you will get a filemanager with root rights.
(sudo works too, but gksudo is preferred for graphical programs.)

EDIT: sorry. noticed that you are using thunar, and not nautilus..
I guess you can start thunar with root rights the same way.

sudo thunar

(xubuntu propably doesnt have gksudo ??)

---

### Post by jis on 2006-08-08
I was trying to copy a customized skin folder to certain application's - namely JAlbum's - skins folder; I had installed JAlbum from JAlbum.net to /opt/JAlbum and the skins folder is a subfolder there. I didn't find cp command so intuitive as I ended up copying the contents (but neither the folder itself nor its subfolders) of the skin folder to the skins folder.

"gksudo thunar" worked for me to copy folder easily and completely.

I'll have to try to remember that gksudo thing. Another possibility would be to develop file managers so that they ask root's password if needed.

---

