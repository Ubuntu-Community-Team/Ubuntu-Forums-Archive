---
title: "disk space?!?!"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-05-19
Please help, my space has been munched!

Why does gnome report seemingly weird disk usage:

Logged in nautilus as root, (with show hidden):

Select all but media and home, right click > properties i get 2.8 Gb
Select home, right click > properties i get 1.9 Gb
..but.. (here's weird phenomenon part 1)
go into home select all and properties i get 4.2GB!?!

(weird phenomenon part 2)
disk is only 19Gb and according to the above and the reported free space (3.5gb) 2.8+4.2+3.5 doesnt add up to 19, 
Unless they have changed the rules of maths, something doesnt add up.

(Weird phenomenon part 3)
I deleted some large files and the disk free space did not change, BUT they were not in trash. Where did they go?

Whats going on with my disk, and how can i accurately get a disk usage report?

---

### Post by meng on 2006-05-19
Do you have a single partition or more than one? From CLI, I think
df
will give you more disk usage statistics.

---

### Post by ubuntu_demon on 2006-05-19
to get a quick overview :
$df -h

To install a graphical tool to view your disk usage :
$sudo apt-get install xdiskusage

To start the tool :
$xdiskusage
$sudo xdiskusage (if you want to be able to view all directories)

to clean some space :
$sudo apt-get clean

---

### Post by steve.horsley on 2006-05-19
also try gnome-system-monitor

---

