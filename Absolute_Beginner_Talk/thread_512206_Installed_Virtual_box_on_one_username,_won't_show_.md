---
title: "Installed Virtual box on one username, won't show up on other."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-07-28
I recently got Virtualbox up and running on one username, with XP going fine.  I then went to another username and it did not appear, only the option to make a new OS virtualbox.  Does anyone know how to get it to show up for the username it's not showing up for?

---

### Post by machoo02 on 2007-07-28
You need to make a new virtual machine, but during the creation (on the "Virtual Hard Disk" dialog page) choose "Existing" instead of "New", and point this at your existing .vdi file.  Be sure to set up this new virtual machine exactly the same as you originally set it up with the first user name.  Also, before you do this you might want to move the .vdi file to somewhere that both users have write access to, since normally the virtual machine files are kept in your /home folder.

Note:  I have not actually done this, but this is how I think it *should* work....

---

### Post by Specter043 on 2007-07-29
Where would be a good place to put the file so we can both write to it?

---

### Post by schorsch on 2007-07-29
> **Specter043 said:**
> Where would be a good place to put the file so we can both write to it?
I would create a new folder "/home/VBox/" for example and then change the permissions so that the group has write access assuming both users are in the same group.  As both users have to be in the group "vboxusers" to run VirtualBox I would try this one.

---

### Post by Specter043 on 2007-07-29
It won't let me create a vbox home folder.  The create folder selection is grayed out.

---

### Post by bsharp on 2007-07-29
Open a terminal and type

sudo mkdir /home/VBox

---

### Post by Specter043 on 2007-07-29
Now that I made that Dir, I don't have permission to write to it.

---

### Post by Specter043 on 2007-07-29
I'm sure it's simple, but I don't know a lot of commands.

---

### Post by machoo02 on 2007-07-29
Enter these commands into a terminal:
```
sudo chgrp -r vboxusers /home/VBox
sudo chmod  -r g+rwx /home/VBox
```

---

