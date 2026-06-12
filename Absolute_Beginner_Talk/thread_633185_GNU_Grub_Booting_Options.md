---
title: "GNU Grub Booting Options"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by mikesalt on 2007-12-06
Hello,

Very new to Linux here, wouldn't really know where to start searching for this so...

90% of the time, I wish my machine to boot up into Windows XP. However, the default in the GNU Grub is to boot in Ubuntu (6.x). It would be preferable to boot in Windows by default. I know that I must go into boot/grub/menu.lst and edit that, and I am pretty sure I know how to edit it. However, when I come to save changes, I am informed that it is 'read-only'. I have been into file properties to try to remove the 'read-only' tick, but this is not accessible. Any ideas how I can edit it?

Thanks,

Mike

---

### Post by Steveway on 2007-12-06
You need to edit it with superuser rights. 
But I would advise you to install startup-manager. It let's you easily choose what to boot first and several other things.

---

### Post by SOULRiDER on 2007-12-06
Toe dit the grub config you need to edit the file as super user, to do so press **alt + f2** and type:
```
gksu gedit /boot/grub/menu.lst
```
You can now edit the file.

---

### Post by mikesalt on 2007-12-06
Steveway, where do I get this startup-manager you speak of?

Thanks

---

### Post by rbprogrammer on 2007-12-06
> **SOULRiDER said:**
> Toe dit the grub config you need to edit the file as super user, to do so press **alt + f2** and type:
```
gksu gedit /boot/grub/menu.lst
```
You can now edit the file.

then i think in the file you need to enable the line that says something like savedefault=false to savedefault=true, or uncomment it, the file should not be too long you will find it.

then go down to the bottom and under the windows entry add in the command "savedefault" and delete the command from the ubuntu entry.

read through the file a little and it will clear up some confusions you may have.  or if you really have trouble with it, post the contents and someone will step you through the process

---

### Post by rbprogrammer on 2007-12-06
> **mikesalt said:**
> Steveway, where do I get this startup-manager you speak of?

Thanks
in GNOME it is "synaptic"
in KDE its "adept"

or go command line:
```

sudo apt-get install startup-manager

```

---

