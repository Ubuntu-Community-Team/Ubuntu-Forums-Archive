---
title: "can't edit file"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by SunRa on 2007-02-12
Hello,

I'm new to linux (xubuntu actualy) and I've allready encontered some problems.

I've tried to mount a ntfs partition but when I edit the fstab file or the pmount file in /etc , the mousepad editor just don't want to save it. When I use a comand like **gksudo gedit /etc/fstab**, I get "command not found".

 So, what's wrong here? Without theese basic commands, I am getting nowhere..

Thanks in advance!

---

### Post by Dr Small on 2007-02-12
try **gksudo nautilus** and browse to the **/etc/fstab** folder and then opening it with gedit then.
Or, **gksudo gedit** and open the file from there.

Dr Small

---

### Post by Bachstelze on 2007-02-12
I don't know what the graphical editor in Xubuntu is, but you could do that from the command line :

*sudo nano /etc/fstab*

When you're done editing, Ctrl+O to save, Enter to confirm and Ctrl+X to exit.

---

### Post by JamieC on 2007-02-12
Well gedit is a graphical editor for the gnome environment...

Try using 'sudo' and a command-line based editor such as nano or vim, the fstab file can only be opened with write privelleges as root, and for that reason 'sudo' is required. Here are some examples:-

```

sudo vim /etc/fstab

```

You can make your changes (use 'i' for insert mode to insert, amend or delete text) and then commit them by typing ':wq' (write and quit).

```

sudo nano /etc/fstab

```

Simply make your changes and then press CTRL + X to quit, it will then prompt you to save your changes, simple type 'Y' and then hit return.

I hope that helps.

---

### Post by nickoli_02 on 2007-02-12
Gedit is a Gnome text editor, you're using XFCE. Try this

```
sudo nano -b /etc/fstab
```

At least, I think you have nano...

In nano, ctrl-x exits. The keystoke listings are along the bottom.

---

### Post by SunRa on 2007-02-12
Thanks guys, I've managed to mount the ntfs partiton...

---

