---
title: "mass transfer of files and not folder in UBUNTU 6.06 LTS"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ogfizzle on 2007-08-09
how do i transfer many files from a folder in my desktop to a folder in root via the command line??:)

---

### Post by AlexenderReez on 2007-08-09
if copy just copy the file....then in terminal

> sudo cp <copied file/of where the file> <place to paste>

if move

> sudo mv <copied file/of where the file> <place to paste>

---

### Post by tgalati4 on 2007-08-09
>sudo cp /home/yourusername/Desktop/yourfolder /yourfolder

---

### Post by Inxsible on 2007-08-09
> **tgalati4 said:**
> >sudo cp /home/yourusername/Desktop/yourfolder /yourfolder

i dont think he wants to move the folder(at least thats what I think)
so i think it should be something like

copy
```
sudo cp /home/yourusername/Desktop/yourfolder/*.* /newFolderName
```or move

```
sudo mv /home/yourusername/Desktop/yourfolder/*.* /newFolderName
``` Of course this will work only if you want to move or copy all the files irrespective of the name and extension. You would have to change it if you only wanted to move/copy jpg files for eg

---

