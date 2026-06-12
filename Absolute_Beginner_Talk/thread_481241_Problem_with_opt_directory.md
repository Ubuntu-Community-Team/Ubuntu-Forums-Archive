---
title: "Problem with /opt directory"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by talrasha on 2007-06-22
Hi all! This is my first time installing XAMPP on Ubuntu to ease my LAMP installation and play with PHP. But when I'm saving my .php file in /opt/lampp/htdocs it gives me this error messages:

> Could not save the file /opt/lampp/etc/original/httpd.conf.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

Can anyone tell me how to save file in this directory? Any help will be gladly appreciated. Thanks! :KS

---

### Post by phr0ze on 2007-06-22
Use the sudo command to copy the file there.

sudo cp httpd.conf /opt/lampp/etc/original/httpd.conf

---

### Post by talrasha on 2007-06-22
Thanks so much! I copied it successfully ^^
But is there a way to make it writable so that I can save my files in that directory using gedit?

---

### Post by Canis familiaris on 2007-06-22
> **talrasha said:**
> Thanks so much! I copied it successfully ^^
But is there a way to make it writable so that I can save my files in that directory using gedit?

You can, just change the permissions but you MUST NOT make /opt directory writeable.

I suggest you set the directory for LAMP within your home directory.

---

### Post by Canis familiaris on 2007-06-22
There's another way which may work (may not work as well)
Create a launcher and in command put: sudo gedit and save in the desktop.
Whenever you need to save in that directory just use that shortcut.

Keep in mind though this is a HUGE security risk.

---

### Post by phr0ze on 2007-06-22
> **Anurag_panda said:**
> There's another way which may work (may not work as well)
Create a launcher and in command put: sudo gedit and save in the desktop.
Whenever you need to save in that directory just use that shortcut.

Keep in mind though this is a HUGE security risk.

IF you are modifying only one file in the folder, make the shortcut edit that one file. Or make a shortcut for the copy command so after any edit you just double click the copy command. Keeping Sudo a requirement makes sure you don't accidentally screw things up or open vulnerabilities since a password will be required for the edit.

Finally if you want to use gedit, use it like this: gksudo gedit /path/file

Dont use sudo for gedit, just gksudo.

I don't see the 'HUGE' security risk with this shortcut. It should still require a password to use it.

---

### Post by talrasha on 2007-06-22
Thanks for the great help guys I really appreciate it and it helps me setup my LAMP environment in Ubuntu.

Ok I'll try those suggestions now. ^^

---

