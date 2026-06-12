---
title: "grub order"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by borz on 2006-03-19
hi 

 how do i change the order in the gurb .ie i want other operating systems to be first on the list  and then amd 64 kernel ?

thanks in advance

---

### Post by Adrian on 2006-03-19
Take a look here:
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by AtinLango on 2006-03-19
If I read you well, you are interested in the order of OSs rather than the default. If so, then open /boot/grub/menu.lst. You can move the block of codes for an OS to a place after another OS.

E.g. move the code block for amd 64 kernel to the end.

---

### Post by borz on 2006-03-19
yup thats what i meant the order of the list . iam very new to all this . how do i bring up the list in ubnutu.

---

### Post by Adrian on 2006-03-19
[QUOTE=borz]yup thats what i meant the order of the list . iam very new to all this . how do i bring up the list in ubnutu.[/QUOTE]

The list is contained in the file **/boot/grub/menu.lst**

You can edit it by typing:

(For GNOME)
```

sudo gedit /boot/grub/menu.lst

```

(For KDE)
```

sudo kwrite /boot/grub/menu.lst

```

However, moving the "menu item blocks" around can mess upp your system if you do something wrong (that's why it's usually better to just change the default value as described in the link I posted above). It's a good idea to backup menu.lst before any changes are done. That way you can easily restore your menu (and system!) by using a live cd, if something goes wrong.

```

cp /boot/grub/menu.lst ~

```
will make a backup in your home directory.

If you are not sure about what you are doing, I'd recommend you to post your menu.lst file here so more experienced users can take a look and suggest what to do.

---

### Post by AtinLango on 2006-03-19
Be careful, don't mess up your system. Do this only if you must.

Open a terminal (Application/Accessories/Terminal) if you are using GNome. This is where you can type commands.

Then one by one type these and press enter:

sudo bash
cd /boot/grub
cp menu.lst menu.lst_backup
nano menu.lst

Now menu.lst is open. If you move downwards, you will see the OS code blocks. Try moving the one you want. You may also want to change the default OS using this file (somewhere at the top). Try.

Then save the file and exit (Ctrl+X), restart the computer and see.
 
NB:
1. After entering sudo bash, this will ask you for password which you created at installation.
2. The third line above is to create a backup of menu.lst just in case.

---

