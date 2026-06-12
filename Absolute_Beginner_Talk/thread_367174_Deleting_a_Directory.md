---
title: "Deleting a Directory"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by mdumka on 2007-02-21
Hello,

I am trying to delete a directory (I un-installed easyubuntu) and it says I do not have permission to do this ... what do I do?

Thanks

Mike

---

### Post by szf on 2007-02-21
Either you don't own the directory, or the error is that the directory isn't empty.

Options:
In a terminal, you could perform:
```
$ sudo rm -ri /usr/local/easyubuntu
```

Or add the Nautilus 'Open As Administrator' script to your system. Then you could graphically navigate to the directory and delete it.

Quickie how-to:
Paste the following into a text editor:
```
#/bin/sh
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

```

Save it to $HOME/.gnome2/nautilus-scripts as 'Open As Administrator'. (You may have to log off-log in, again).

Open Nautilus. Select a directory and right-click the mouse. Select Scripts -> Open As Administrator (you did save it as that name, right?) and enter your password when prompted. Navigate to the directory that EasyUbuntu is installed and delete it as Admin.

---

### Post by Maestro23 on 2007-02-21
.

---

