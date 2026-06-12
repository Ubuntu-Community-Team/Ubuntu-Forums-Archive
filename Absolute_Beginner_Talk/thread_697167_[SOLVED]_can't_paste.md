---
title: "[SOLVED] can't paste"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-14
why would ubuntu or certain folders or whatever restrict my ability to paste something into them? i am the administrator, seeing as i'm the only person who uses my computer, and yet there are so many places where it tells me that i "don't have permissions to write to this folder". how do i fix this?

---

### Post by LaRoza on 2008-02-14
> **Sinkingships7 said:**
> why would ubuntu or certain folders or whatever restrict my ability to paste something into them? i am the administrator, seeing as i'm the only person who uses my computer, and yet there are so many places where it tells me that i "don't have permissions to write to this folder". how do i fix this?

Ok, you are not the administrator, you are a user.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Where are you trying to copy to? If it isn't an external drive or another partition, your most likely shouldn't be copying there.

The only place where you can have write access is your home directory usually.

---

### Post by Sinkingships7 on 2008-02-14
my situation is this: i'm just trying to install a different lock screen (the screen that shows up if you lock your computer) by pasting files i downloaded into the 'gnome-screensaver' folder under usr/share/gnome-screensaver.

---

### Post by spiderbatdad on 2008-02-14
If you are trying to edit a basic text file in the system, for example a config file, or menu.lst, you would open that file with a text editor having administrative privileges, commonly gedit is used for these basic text files. gksu is the command to open a graphical app with sudo privileges...so...```
gksu gedit /boot/grub/menu.lst
```
Would open /boot/grub/menu.lst with sudo privileges. You would have permission to write to the file.

---

### Post by spiderbatdad on 2008-02-14
> **Sinkingships7 said:**
> my situation is this: i'm just trying to install a different lock screen (the screen that shows up if you lock your computer) by pasting files i downloaded into the 'gnome-screensaver' folder under usr/share/gnome-screensaver.

That is a directory. the above post wouldn't apply. In that case I sometimes temporarily change permissions of the directory. Logging in as root works, too

---

### Post by LaRoza on 2008-02-14
> **spiderbatdad said:**
> That is a directory. the above post wouldn't apply. In that case I sometimes temporarily change permissions of the directory. Logging in as root works, too

Don't log in as root, use:

```

gksudo nautilus

```

But be very, very careful!

---

### Post by Sinkingships7 on 2008-02-14
i tried to temporarily change permissions by right clicking the folder, going to properties, and going to the permissions tab. this has worked for other things in the past, but the whole menu just says root and the drop downs are grayed out. to login as root, do i just type "root" as the username, and my password?

---

### Post by Sinkingships7 on 2008-02-14
what does that code do?

---

### Post by LaRoza on 2008-02-14
> **Sinkingships7 said:**
> what does that code do?

It runs nautilus as root.

If you do that, you will be able to access the files. You can do the right click thing to change permissions as well. I don't recommend changing permissions, just do what you have to do and get out.

(You can't log in as root on Ubuntu by default)

---

### Post by Sinkingships7 on 2008-02-14
> **LaRoza said:**
> It runs nautilus as root.

If you do that, you will be able to access the files. You can do the right click thing to change permissions as well. I don't recommend changing permissions, just do what you have to do and get out.

thank you. just wanted to be safe :)

---

