---
title: "how do I gain permission to paste files where I want"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-07-22
I'm trying to paste a font into wines fonts folder, but it says I do not have permission.

I tried right-clicking -> properties. But the drop down menu is painted out.

any help appreciated

---

### Post by xpod on 2007-07-22
Open a terminal or alt-f2 and type in 
```
gksudo nautilus
```
This opens nautilus with root permission but be careful what you edit and change like this,especially outwith your home directory:)

For editing files as root do
```
gksudo gedit path/to/file/name
```

---

### Post by Ludford on 2007-07-22
OK, Ive done that but when I go to usr/share/wine/fonts Paste is still not clickable.

---

### Post by sunshine12 on 2007-07-22
You need to be root (administrator) to do some system stuff..

do this, in terminal ( to bring terminal, press alt+F2, write gnome-terminal and hit enter)

```
sudo cp SOURCE_FILE.ttf DESTINATION
```

or type 

```
gksudo nautilus
```
for administrative application in nautilus

---

### Post by sunshine12 on 2007-07-22
May be you should look at this page

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by weblordpepe on 2007-07-22
As I recall you can't drag/drop accross nautilus windows that are as different users.

That means you cant drag a file from your normal file window into one running as root. Unless you're superman. Superman is the only one that can beat up root.

---

### Post by weblordpepe on 2007-07-22
woops double post.

---

### Post by Daveth on 2007-07-22
it will be, in terminal,

sudo cp /home/ludford/downloads or wherever/tahoma.ttf      /home/ludford/.wine/drive_c/windows/fonts

note that thwe wine folder has a . before it, so is one of those hidden folders in your /home/ludford folder. You can use ctrl+h to unhide them all.

---

