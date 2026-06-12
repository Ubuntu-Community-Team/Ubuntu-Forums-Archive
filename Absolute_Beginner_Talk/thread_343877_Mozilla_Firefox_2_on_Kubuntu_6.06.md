---
title: "Mozilla Firefox 2 on Kubuntu 6.06"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by diazemmanuel on 2007-01-22
I just got my Kubuntu 6.06 disks for 32-bit PCs. I installed it as a dual boot OS alongside my WinXP. I am trying to familiarize myself with the new OS. (Nice is my initial impression).

I wanted to install Mozilla Firefox 2.0. I've downloaded the tarball for 2.0.0.1 already. Followed instructions on the debianadmin site for installing Firefox 2.0. At the last command, Firefox didnt appear. Did I do anything wrong? Help. Many thanks.

---

### Post by Canis familiaris on 2007-01-22
(1) Download the tarball from [getfirefox.com]("http://www.getfirefox.com/") (I guess you've done that already.
(2) Copy it to your home folder.
(3) Go to terminal:
```
tar xvzf fire*

```
A firefox folder will be created on your home folder.
(4) Now open konqueror as root, in terminal:
```
sudo konqueror /opt

```
(5) Copy the firefox folder on the /opt directory.
(6) Now you can run firefox by command in terminal:
```
/opt/firefox/firefox
```
(7) Create a launcher in your desktop and edit the K Menu and add a firefox launcher using the above command for launching firefox

AND Browse the net using Firefox. :-\"

---

