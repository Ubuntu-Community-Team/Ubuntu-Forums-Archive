---
title: "sudo and folder write permissions"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by arborealguy on 2006-09-09
Hey all. So I want to put something in /ect, but of course, without sudo I don't have the permissions. What command do I use so I can get the write permissions and either do it in the GUI or with the terminal (the actual moving)?

---

### Post by blackened on 2006-09-09
> What command do I use so I can get the write permissions and either do it in the GUI
gksudo nautilus
> or with the terminal (the actual moving
sudo gedit /etc/*filename* - if you want to create a new empty file
sudo mv *filename /etc/filename* - if the file exists and you want to move it.
sudo cp *filename /etc/filename* - same as mv, but leaves the old file where it was.

To open a root command line so you don't have to precede every command with *sudo* use *sudo -i*.

---

