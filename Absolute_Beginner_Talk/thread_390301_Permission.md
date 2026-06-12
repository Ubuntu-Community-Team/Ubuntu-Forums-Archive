---
title: "Permission?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Cokeman on 2007-03-21
I'm new to Ubuntu so not sure how I can do this. With the older Linux I used I had root access to files. With Ubuntu I don't. I have some files/folders I created I need to delete but can't cause owner is root. How can I make it so I have root owner ship? Thanks.

---

### Post by The Mekon on 2007-03-21
The easiest way is when in the terminal enter:

sudo su

You will be asked for your password and, if correct, you are in as root.

For single operations

sudu "comand" is safer as it reverts to the normal user after executing the command.

Don't forget the enter exit to cancel the root mode.

---

### Post by Cokeman on 2007-03-21
Thanks, I can get root access to terminal, but how can I delete the folder/files. The have a padlock over them so I know I don't have permission. I also have folders/files I need to edit but can't cause I'm not owner. I basically need root access to all files. Its not a security problem cause I only use Linux to mod my cellphone files. These are the files/folders I need access to but don't know how.

---

### Post by sad_iq on 2007-03-21
> **The Mekon said:**
> The easiest way is when in the terminal enter:

sudu "comand" is safer as it reverts to the normal user after executing the command.

 That's **sudo** "comand" ... just so you don't get confused
 And also there is the **sudo -s -H** ...that will keep your home directory!!!

---

### Post by sad_iq on 2007-03-21
You could also open nautilus as root...try ALT+F2 ...put **gksudo nautilus**...and that should do it!!

---

### Post by Cokeman on 2007-03-21
Thanks I'll try the sudo -s -H & nautilus see which one does the trick.

---

### Post by dracomordag on 2007-03-21
yea, all it should take is sudo nautilus


if you want to permenantly change the permissions, navigate to the directory in the terminal and chmod the folder.

---

