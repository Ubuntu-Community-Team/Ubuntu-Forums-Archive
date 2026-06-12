---
title: "Question about using Terminal-shortcut to directory"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2007-07-08
How do you make a shortcut to go to the directory you want?
for example. whenever I open the terminal, i don't want to type the whole directory structure
~/a/b/c/d/e/f/g/h/ until i find the content of what's inside h

is there a way for me to avoid all these?
Thanks

---

### Post by aysiu on 2007-07-08
Well, if you navigate through the GUI to *g*, you can type ```
cd
``` in the terminal and drag the *h* folder to the terminal.

If the folder names are longer than one letter, you can type part of each folder name and then hit the **Tab** key to autocomplete.

---

### Post by Vajra Vrtti on 2007-07-08
I thing the easiest way is to install the package **nautilus-open-terminal,** which will permit you to right click any folder in Nautilus and open a terminal windows already positioned in that folder.

---

### Post by taisao on 2007-07-08
oh, nice. I will try nautilus-open-terminal too.
--

If you are using the gnome-terminal you can create a application laucher like this

gnome-terminal --working-directory /media/

so when the terminal fire up, the working directory is /media/ and not /home/username/

---

### Post by boom2k1 on 2007-07-08
Thanks guys. The gnome working directory is kind of what I am looking for.. but I am just wondering whether there is a more intuitive way to map folder.. like what I want to accomplish in a desktop shortcut to a deep folder.

Thanks

---

### Post by taisao on 2007-07-08
you could make a shortcut like this

username@username-desktop:~$ **ln -s ~/a/b/c/d/e/f/g/h/ linkToH**

after that you could use **cd linkToH** instead of **cd ~/a/b/c/d/e/f/g/h/ **

---

### Post by boom2k1 on 2007-07-10
Thanks! Exactly what I am looking for !

---

