---
title: "connot delete file"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by royal314 on 2007-04-01
I wanted to install xdvdshrink and the only way i could install it was as a .rpm file, so i converted that to a .deb using alien and tried to install it but it said it couldn't install it. because i didn't want to mess with it i tried deleting the files but now it says i don't have permissions to delete the file. any suggestions?

---

### Post by Spr0k3t on 2007-04-01
have you tried to delete the specific file with a sudo command?

---

### Post by royal314 on 2007-04-01
which sudo command would i use?

---

### Post by royal314 on 2007-04-01
i mean't to ask what command is used to delete files

---

### Post by Dual Cortex on 2007-04-01
rm = remove a file
rmdir = remove a directory

sudo rm [nameOfFile..or pathToFIle/nameOfFile]

---

### Post by Maestro23 on 2007-04-01
If you didn't install it:  rm filename

If you installed the .deb pkg, then: 

sudo dpkg -r packagename (leaves dependencies)

sudo dpkg -P packagename (deletes dependencies)

---

### Post by royal314 on 2007-04-01
thanks for the replies.

I tried what you said but it still won't work, when i try to remove the directory ii says that the directory isn't empty and it won't remove it. when i try to remove it as a file it says it is a directory? i've never had this problem before, do i need to change the permissions somehow?

---

### Post by Dual Cortex on 2007-04-01
Make sure you change position inside the terminal to that directory to delete the file. Let me show you an example

Lets say you have a directory in /home called myDir. Inside that directory you have a file called myFile.jpg.

Now open a terminal window. It's default directory when opened is /home/[username]. Anyway, lets delete the file. You need to input the following commands:
> cd /home/myDir/
rm myFile.jpg
You could have had also skipped a step there by typing
> rm /home/myDir/myFile.jpg

Now that the directory is empty you can simply type the following to delete it:
> cd /home/
rmdir myDirectory
or
> rmdir /home/myDirectory

if you wanted to remove the directory and all files inside it in less steps you could have issued:
> cd /home/
rmdir -r myDir
or
> rmdir -r /home/myDIr

You could also have done all this graphically by issuing:
> gksudo nautilus
and just browsing to the file or directory you want to delete. This isn't recommended because you have the power to delete ANY file... and... you don't want to delete necessary files of the system by mistake.

---

### Post by royal314 on 2007-04-01
thanks for the help but i still must be donig something wrong...

thre is a folder on my desktop titled "xdvdshrink-2.6.1" and it has a lock symbol by it. this is what i'm trying to delete. when I try to delete it by right clicking it says i don't have the right permissions. also i havn't been able to do it in the terminal so i think i'm doing something wrong, when I tried the "gksudo nautilus" the file would not show up

---

### Post by Maestro23 on 2007-04-01
Did you try:

> sudo rm -r xdvdshrink-2.6.1

---

### Post by royal314 on 2007-04-01
thanks, finally got it work

---

### Post by Maestro23 on 2007-04-01
> **royal314 said:**
> thanks, finally got it work

Good deal.

---

