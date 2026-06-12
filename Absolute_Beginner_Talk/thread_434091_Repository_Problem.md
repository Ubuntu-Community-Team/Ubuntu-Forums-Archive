---
title: "Repository Problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-05
Hi there, I was attempting to setup VLC player and didn't put deb in front of something before I hit enter and now I'M getting this when I try to add/remove programs:
E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory

I tried to go in and delete the line but it's read only and it's not letting me save the sources with that line removed. ANy help??

---

### Post by useResa on 2007-05-05
You can edit your file by "taking the roll" of root.
In order to edit the file as root, give the following command in a terminal (Applications --> Accessories --> Terminal)```
gksudo gedit /etc/apt/sources.list
```
Now you can edit the file by either deleting the line or put the word deb in front of the line.
Next save the file and close the text editor.

After this you need to give the following command in the terminal
```
sudo apt-get update
```
To "read" the content of your altered sources.list

Hope this will help you. Good luck.

---

### Post by Tumpster on 2007-05-05
> **useResa said:**
> You can edit your file by "taking the roll" of root.
In order to edit the file as root, give the following command in a terminal (Applications --> Accessories --> Terminal)```
gksudo gedit /etc/apt/sources.list
```
Now you can edit the file by either deleting the line or put the word deb in front of the line.
Next save the file and close the text editor.

After this you need to give the following command in the terminal
```
sudo apt-get update
```
To "read" the content of your altered sources.list

Hope this will help you. Good luck.



Worked, thank you!!

---

