---
title: "Installing BIN files"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by BottomsMU on 2006-04-16
I am trying to install MONO and some other programs.  I saved the bin files to the desktop.  I read the install notes here
[http://www.mono-project.com/InstallerInstructions](http://www.mono-project.com/InstallerInstructions)
but I don't know how to point to the right directory.

Lil help plz? ](*,)

---

### Post by malavar on 2006-04-16
sudo sh file.bin

or for the ubuntu packages:
sudo apt-get install mono

---

### Post by BottomsMU on 2006-04-16
Thanks, i used the 2nd line.  BUt how did ubuntu recognize the bin file and where it was?

---

### Post by BottomsMU on 2006-04-16
also, it installed, but where do i find it?

---

### Post by malavar on 2006-04-16
type 'mono' in the terminal , use the whereis command to locate the binary i.e
whereis mono

---

### Post by BottomsMU on 2006-04-16
Thanks, but how do i open the program so i can edit visual basic projects and form files?

---

### Post by sn123 on 2006-04-16
[QUOTE=BottomsMU]Thanks, but how do i open the program so i can edit visual basic projects and form files?[/QUOTE]
$ sudo apt-get install monodevelop
then 
$ monodevelop
or Applications-->Programs-->monodevelop

---

