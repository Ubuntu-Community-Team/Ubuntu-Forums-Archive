---
title: "How can you edit the xorg.conf file?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by thisdevil on 2007-04-25
I need to know how to access the xorg.conf file so i can edit it and save the changes ive made to fix some problems i have. can anyone give me some in site on this? I have found the file and opened it but it wont let me save. please help.

---

### Post by BoneKracker on 2007-04-25
You have to be root to write that file.  

Use sudo to temporarily gain root privileges while you have the editor open.  Type one of the following into the terminal.```
sudo gedit /etc/X11/xorg.conf

```or```
sudo nano /etc/X11/xorg.conf
```
(Gedit has menus and buttons.  In nano, use ctrl+o to save; ctrl+x to exit.)

---

### Post by ljcasey on 2007-04-25
make sure to back it up...

---

### Post by shavenlunatic on 2007-04-25
> **ljcasey said:**
> make sure to back it up...

to do this:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

case sensitive

---

