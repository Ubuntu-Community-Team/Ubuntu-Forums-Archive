---
title: "folders on my desktop that I can't delete"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-06-02
I have a couple of folders on my desktop that I can't delete. When I drag any of them into trash I get a message that says permission denied. Also when I right click on them the delete option is not highlighted. Is there an other way?

---

### Post by Ek0nomik on 2007-06-02
You must have created the folders using sudo or logging in as root.

You can delete the folders via command line or graphically.  I will show you how to do it both ways:

Open a terminal and type:

```
cd Desktop
ls
sudo rmdir your.directory.name
```

or

```
gksudo nautilus
```

With the last command, you can simply right click and hit delete.  The first way is also just as easy depending on what you are comfortable with.  :)

**Note**:  If the directories aren't empty, you will probably get an error telling you so if you try to delete via rmdir command.  If you want to delete the folder with files in it, run this command:

```
sudo rm -r your.directory.name
```

---

### Post by mikewhatever on 2007-06-02
What folders are they? Can you post a screenshot? Have you created those folders, or were they there after the installation? Are they, by chance, called sda1, sda2 or similar?

---

### Post by Ek0nomik on 2007-06-02
Ahhhhh.  Can you unmount them?  Do you have USB devices plugged into your computer?  That is more than likely what they are.

If you want to hide volumes (usb devices, cd-rom, etc) from showing up on you desktop there is an easy fix.

Open a terminal and type:

```
gconf-editor
```
Apps >> Nautilus >> Desktop >> Uncheck "Volumes Visible"

---

### Post by Malta paul on 2007-06-02
You could try to right clicking the file >permission>owner-access and Change to 'Read and Write' It might be read only?

---

### Post by muggins on 2007-06-02
[QUOTE=Ek0nomik;2766181]You must have created the folders using sudo or logging in as root.

You can delete the folders via command line or graphically.  I will show you how to do it both ways:

Open a terminal and type:

```
cd Desktop
ls
sudo rmdir your.directory.name
```

or

```
gksudo nautilus
```

With the last command, you can simply right click and hit delete.  The first way is also just as easy depending on what you are comfortable with.  :)

I typed "gksudo thunar" and then right clicked and hit delete, that did the trick.
Thanks for your replies everyone.

---

### Post by matteospqr on 2007-06-09
Guys I have the same problem.  I cant do stuff on my desktop.  It says I dont have the right to download stuff and save it there but before I could do it without any problems.  Now even the folders that are on my desktop or some files (ex. jpg) cannot be touched, moved, or deleted.

Is there a way to set the desktop free?

Thanks!

---

### Post by davidwarren on 2007-06-09
> **Ek0nomik said:**
> Ahhhhh.  Can you unmount them?  Do you have USB devices plugged into your computer?  That is more than likely what they are.

If you want to hide volumes (usb devices, cd-rom, etc) from showing up on you desktop there is an easy fix.

Open a terminal and type:

```
gconf-editor
```
Apps >> Nautilus >> Desktop >> Uncheck "Volumes Visible"

Thanks! Couldn't figure how to get those drives off the desktop.

edit
actually......
the drives I was concerned about removing from the desktop were sda1 and sda2, but I still would like to see cd/dvd/usb drives I mount. Is there a way to do that?

---

