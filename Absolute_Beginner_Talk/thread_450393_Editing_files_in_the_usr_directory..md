---
title: "Editing files in the usr directory."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Aryra on 2007-05-21
I'm NOT a complete beginner, so feel free to just spurt out terminal commands at me...but I couldn't see anywhere for this topic to go.

I'm trying to install some addons into celestia, but I cant paste into the correct directory, because its in /usr/...which I cant edit.

Help?

---

### Post by icechen1 on 2007-05-21
try > sudo nautilus

this will make you run the file manager in root mode.If you are using KDE change it the the kde one.

---

### Post by 3rdalbum on 2007-05-21
```
gksudo nautilus
```

Within the Nautilus window that opens, you will be able to modify any file on the filesystem. You can drag files onto the new window to copy them into /usr/.

Just make sure you close the window after you've finished the tasks you need to perform as root.

EDIT: If you're running KDE, change it to:

```
kdesu konqueror
```

If you're running Xubuntu, change it to:

```
gksudo thunar
```

---

### Post by Bachstelze on 2007-05-21
sudo is your friend ;)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by justleen on 2007-05-21
try starting a root-nautilus ```
gksudo nautilus
```
copy paste again..(hint: make a shortcut for that command :) )

Alternative is to copy from the commandline..
```
 sudo cp -r /home/user/yourfiles/* /usr/share/celestia 
```

---

### Post by Aryra on 2007-05-22
Ahhh, of course. Duh, how stupid am I :P

Okies, thanks everyone ^^

---

